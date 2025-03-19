<script setup>
import { resolveDirective } from "vue";

const props = defineProps({
  percentages: {
    txpe: Array,
    default: [0, 0, 0],
  },
});
//                rot         blau       gelb
const colors = ["#ff6384", "#36a2eb", "#ffce56"];
const labels = ["Kohlenhydrate", "Proteine", "Fette"];

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

let cumulativeAngle = 0;
const arcs = props.percentages.map((percentage, index) => {
  const angle = (percentage / 100) * 360;
  const startAngle = cumulativeAngle;
  const endAngle = cumulativeAngle + angle;
  cumulativeAngle += angle;
  return {
    d: describeArc(50, 50, 40, startAngle, endAngle),
    fill: colors[index % colors.length],
  };
});
</script>

<template>
  <div class="flex flex-col items-center">
    <div class="flex justify-center">
      <svg width="200" height="200" viewBox="0 0 100 100">
        <circle cx="50" cy="50" r="40" fill="#ddd" />
        <path
          v-for="(arc, index) in arcs"
          :key="index"
          :d="arc.d"
          :fill="arc.fill"
          stroke="#fff"
          stroke-width="1"
        />
      </svg>
    </div>
    <div class="mt-4">
      <ul>
        <li
          v-for="(label, index) in labels"
          :key="index"
          class="flex items-center space-x-2"
        >
          <span
            :style="{ backgroundColor: colors[index] }"
            class="w-4 h-4 inline-block"
          ></span>
          <span>{{ label }} ({{ percentages[index] }}%)</span>
        </li>
      </ul>
    </div>
  </div>
</template>
