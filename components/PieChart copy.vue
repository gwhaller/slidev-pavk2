<script setup>
import { ref, computed, watch, onMounted, onUnmounted } from "vue";
import { useTransition } from "@vueuse/core";

const props = defineProps({
  percentages: {
    type: Array,
    default: () => [33, 33, 34], // Ensure a default value exists
  },
  shrink: {
    type: Boolean,
    default: false, // Standardmäßig normale Größe
  },
  open: {
    type: Boolean,
    default: false, // Steuert die Animation
  },
});

// 🎨 Colors and labels
// const colors = ["#ff6384", "#36a2eb", "#ffce56"];
const fillColors = ["fill-red-500", "fill-blue-500", "fill-yellow-500"];
const bgColors = ["bg-red-500", "bg-blue-500", "bg-yellow-500"];
const labels = ["Kohlenhydrate", "Proteine", "Fette"];

// 🎯 Start segments with a minimal value (1%)
const animatedPercentages = ref(props.percentages.map(() => 0));

// 🚀 Animation with `useTransition`
const transition = useTransition(animatedPercentages, {
  duration: 500,
  transition: [0.25, 0.1, 0.25, 1],
});

// 🎬 Start animation
const startAnimation = () => {
  animatedPercentages.value = [...props.percentages];
};

// 🎬 Reset animation
const resetAnimation = () => {
  animatedPercentages.value = props.percentages.map(() => 0); // Reset to initial values
};

// 🔄 Watch for props changes
watch(
  () => props.percentages,
  (newValues) => {
    animatedPercentages.value = newValues.map((val) => Math.max(val, 1)); // Prevent 0 values
  },
  { immediate: true },
);

// 🎯 SVG helper functions
const polarToCartesian = (centerX, centerY, radius, angleInDegrees) => {
  const angleInRadians = ((angleInDegrees - 90) * Math.PI) / 180.0;
  return {
    x: centerX + radius * Math.cos(angleInRadians),
    y: centerY + radius * Math.sin(angleInRadians),
  };
};

const describeArc = (x, y, radius, startAngle, endAngle) => {
  const start = polarToCartesian(x, y, radius, startAngle);
  const end = polarToCartesian(x, y, radius, endAngle);
  const largeArcFlag = endAngle - startAngle <= 180 ? "0" : "1";
  return `M ${start.x},${start.y} A ${radius},${radius} 0 ${largeArcFlag},1 ${end.x},${end.y} L ${50},${50} Z`;
};

// 🏹 Compute animated arcs
const arcs = computed(() => {
  if (!transition.value) return []; // Ensure transition exists

  let cumulativeAngle = 0;
  return transition.value.map((percentage, index) => {
    const angle = (percentage / 100) * 360;
    const startAngle = cumulativeAngle;
    const endAngle = cumulativeAngle + angle;
    cumulativeAngle += angle; // New segment starts at the end of the previous one

    return {
      d: describeArc(50, 50, 49, startAngle, endAngle),
      class: fillColors[index % fillColors.length],
    };
  });
});

// 🎬 MutationObserver to detect class changes
const targetElement = ref(null);
let observer;

// 🎬 MutationObserver to detect grandparent display changes
let grandparentObserver;

onMounted(() => {
  // Initialize animatedPercentages with minimal values
  animatedPercentages.value = props.percentages.map(() => 0);

  // Set up the MutationObserver for class changes
  observer = new MutationObserver((mutationsList) => {
    for (const mutation of mutationsList) {
      if (
        mutation.type === "attributes" &&
        mutation.attributeName === "class"
      ) {
        const hasBothClasses =
          targetElement.value.classList.contains("slidev-vclick-current") &&
          targetElement.value.classList.contains("slidev-vclick-target");

        if (hasBothClasses) {
          startAnimation(); // Start the animation when both classes are present
        }
      }
    }
  });

  // Start observing the target element for class changes
  if (targetElement.value) {
    observer.observe(targetElement.value, {
      attributes: true, // Monitor attribute changes
      attributeFilter: ["class"], // Only monitor class changes
    });
  }

  // Set up the MutationObserver for grandparent display changes
  const grandparentElement = targetElement.value?.parentElement?.parentElement;
  if (grandparentElement) {
    grandparentObserver = new MutationObserver((mutationsList) => {
      for (const mutation of mutationsList) {
        if (
          mutation.type === "attributes" &&
          mutation.attributeName === "style"
        ) {
          const isHidden = grandparentElement.style.display === "none";
          if (isHidden) {
            resetAnimation(); // Reset the animation when grandparent is hidden
          }
        }
      }
    });

    // Start observing the grandparent element for style changes
    grandparentObserver.observe(grandparentElement, {
      attributes: true, // Monitor attribute changes
      attributeFilter: ["style"], // Only monitor style changes
    });
  }
});

// Clean up the observers when the component is unmounted
onUnmounted(() => {
  if (observer) {
    observer.disconnect();
  }
  if (grandparentObserver) {
    grandparentObserver.disconnect();
  }
});
</script>

<template>
  <div ref="targetElement" class="flex">
    <div
      :class="{ 'scale-70': props.shrink, 'scale-100': !props.shrink }"
      class="transition-transform duration-300"
    >
      <svg width="200" height="200" viewBox="0 0 100 100">
        <circle cx="50" cy="50" r="49" fill="#ddd" />
        <path
          v-for="(arc, index) in arcs"
          :key="index"
          :d="arc.d"
          :class="[arc.class]"
          stroke="#fff"
          stroke-width="1"
        />
      </svg>
    </div>
    <div class="flex flex-col">
      <div class="mt-auto">
        <ul>
          <li
            v-for="(label, index) in labels"
            :key="index"
            class="flex items-center space-x-2"
          >
            <span :class="['w-4 h-4 inline-block', bgColors[index]]"></span>
            <span>{{ label }}</span>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
