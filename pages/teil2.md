---
title: meiden
layout: two-cols
clicks: 2
---

# Ernährung

## Vorsicht bei ...

<div class="mt-6 h-50">
  <img src="/images/raffinierte-kh.jpg" />
  <line-md:remove v-if="$clicks >= 1" class="abs-tl size-90 top-30 left-24" style="color: #d91d1d"/>
  <div class="mt-6">Kohlenhydraten / Zucker</div>
</div>

::right::

<div>
  <line-md:remove v-if="$clicks >= 2" style="color: #d91d1d" class="abs-tr size-90 right-25 top-26"/>
  <img src="/images/sonnenblumenöl.webp" class="size-100"/>
  <div class="mt-6 ml-12">industriell hergestellte pflanzliche Öle<br>( z.B. Sonnenblumenöl )</div>
</div>

---

<br><br>

## Das Problem mit den

# Ernährungsempfehlungen

---
title: Dynamisches SVG Kuchendiagramm
---

<div class="relative mt-20">
  <PieChart class="abs-tl":percentages="[10, 30, 60]"></PieChart>
</div>

---

# DGE-Ernährungs-

# Empfehlungen 2025

<img src="/images/dge-ernaehrungskreis.webp" class="size-130 abs-tr top-5 right-10"/>
<br>

- überwiegend Kohlenhydrate und Zucker
- balaststoffreich
- viel Getreide
- wenig Proteine
- wenig Fette

<span class="abs-bl left-10 pb-4">DGE (Deutsche Gesellschaft für Ernährung e.V.)</span>

---

### Die Cholesterinhypothese

<v-clicks>

- 1913: Nikolai Anitschkow Kaninchen-Versuch mit tierischer Nahrung
- 1950er: in den USA sterben bald eine halbe Million Menschen jedes Jahr an einem Herzinfarkt
- 1955: US-Präsident Dwight D. Eisenhower einen Herzanfall, den er knapp überlebt
- Ancel Keys (University of Minnesota): Diet-Heart-Hypothesis<br>
  -> Vergleich vom Fettkonsom in 6-7 Länder in 2 Studien<br>
- George Mann: Framingham-Heart-Study<br>
  -> Massai-Krieger (Fleisch, Milch und Rinderblut) trotzdem keine Gefäßerkrankungen
- 1970er: John Yudkin (University of London)<br>
  sieht raffinierte Kohlenhydrate, insbesondere Zucker als das Hauptproblem
- 1980 Dietary Guidelines (allen Menschen wird eine fettarme Ernährung empfohlen)<br>
  - Margarine statt Butter, Fettarme Milch, Joghurt, Quark und Käse
  - Seefisch und Nüsse werden zu "Dickmacher"
  - Vermehrter Einsatz von raffinierten Speiseölen (reich an Omega-6 Fettsäuren) und Zucker
- 2007 Professor Gardner A to Z Study - Low-Carb-Diät<br>
  - Cholesterin stieg, Trigyceride halbiert, Gewichtsabnahme, Blutdruckabnahme

</v-clicks>

---
layout: image
image: /images/folgen_den_richtlinien_1.jpeg
backgroundSize: 30rem
---

---
layout: image
image: /images/folgen_den_richtlinien_2.jpeg
backgroundSize: 30rem
---

---
layout: image
image: /images/folgen_den_richtlinien_3.jpeg
backgroundSize: 30rem
---

---
layout: image
image: /images/folgen_den_richtlinien_4.jpg
backgroundSize: 40rem
---

---
layout: image
image: /images/Übergewicht-in-den-USA.jpg
backgroundSize: 70%
---

## Die Cholesterinhypothese

---
title: Helsiki Businessmen Study
---

<img src="/images/helsinki.png" class="w-170 abs-tl top-5 right-10"/>

<div class="bg-red-500/50 w-58 h-4 abs-tl top-13 left-40" />
<div v-click=12 class="bg-red-500/50 w-18 h-4 abs-tl top-97 left-26" />
<div  v-click=13 class="text-blue-900 abs-tl left-8 top-100 font-black" v-motion :initial="{ y: 80 }" :enter="{ y: 0 }">Reduktion des Herzinfarkt-Risikos</div>
<div v-click=14 class="bg-red-500/50 w-12 h-4 abs-tl top-90 left-142" />
<div v-click=14 class="bg-red-500/50 w-15 h-4 abs-tl top-94 left-99" />
<div  v-click=15 class="text-red-600 abs-tl left-89 top-100 font-black" v-motion :initial="{ y: 80 }" :enter="{ y: 0 }">führte zur erhöhten Sterblichkeit</div>

<span v-mark="{ at: 1, color: 'green', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-53 ml-6">XXXXXXXXXX</span>
<span v-mark="{ at: 2, color: 'green', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-56 ml-6">XXXXXXXX..</span>
<span v-mark="{ at: 3, color: 'green', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-56 ml-33">XX.</span>
<span v-mark="{ at: 4, color: 'green', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-56 ml-47">XXXXX.</span>
<span v-mark="{ at: 5, color: 'red', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-60 ml-17">XXXXX.</span>
<span v-mark="{ at: 6, color: 'red', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-60 ml-34">XX..</span>
<span v-mark="{ at: 7, color: 'red', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-60 ml-48">XXXXXXXXXXX</span>
<span v-mark="{ at: 8, color: 'blue', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-63 ml-6">XXXXXXXXXXX.</span>
<span v-mark="{ at: 9, color: 'blue', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-63 ml-47">XXXXX.</span>
<span v-mark="{ at: 10, color: 'blue', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-67 ml-6">XXXXXXXXX</span>
<span v-mark="{ at: 11, color: 'blue', type: 'underline', strokeWidth: '4' }" class="text-transparent abs-tl mt-70 ml-6">XXXXXXXXX</span>

<div class="abs-tr right-20">
<div class="mt-4 text-green">mehr</div>
<v-clicks>

- Sport/Bewegung
- Gemüse
- Früchte
- Vollkornprodukte

</v-clicks>

<div class="mt-4 text-red">weniger</div>
<v-clicks>

- gesättigte Fetten
- Süßigkeiten
- gezuckerte Getränke

</v-clicks>
<br>
<v-clicks>

- Gewichtskontrolle
- Rauchen einstellen
- Blutdruck
- Cholesterinsenker

</v-clicks>

</div>

---

<br><br>

## Das Problem mit den

# **Studien**

---
title: Tante Emma
layout: image
image: /images/TanteEmma.jpg
backgroundSize: contain
---

---
layout: image
image: /images/1961.jpg
backgroundSize: 40%
title: AncelKeys
---

---

<br><br>

## Das Problem mit den

# **sekundären Pflanzenstoffen**

---
layout: image
image: /images/sekundaerePflanzenstoffe.jpeg
backgroundSize: 100%
title: Sekundäre Pflanzenstoffe
---

---
layout: image
image: /images/Biochemie.jpeg
backgroundSize: 100%
title: biochemie
---

---
title: Massai
layout: image
image: /images/massai.jpg
backgroundSize: contain
---

---
title: Inuit
layout: image
image: /images/inuit.jpg
backgroundSize: contain
---

---

<br><br>

## Das Problem mit den

# **Proteinen**

---
layout: image-right
image: /images/baustoffe.webp
---

# Proteine = Eiweiß

<span class="*:size-12 *:mx-2">
  <twemoji-cut-of-meat />
  <emojione-v1-fish />
  <fluent-emoji-flat-glass-of-milk />
  <twemoji-cheese-wedge />
  <emojione-egg />
  <twemoji-beans />
  <img src="/icons/walnut.png" class="inline-block align-top"/>
</span>

<br>
<br>

### Baustoff

#### kann nicht gespeichert werden

<br>
<v-clicks>

- Reparatur
- Organe, Muskeln, Knochen, Gelenke, Haut
- Antikörper
- Enzyme
- Hormone
- Transport

</v-clicks>

---

<br><br>

## Das Problem mit den

# **Fetten**

---

<div class="grid grid-cols-2 gap-4">

<div>

## Fett

<br>

<v-click>

### gesättigte Fettsäuren

</v-click>

<div class="flex justify-between mb-20">
  <div v-click=1 class="flex space-x-2xl *:size-12">
    <img class="size-12" src="/icons/butter2.png"/>
    <noto-v1-bacon/>
    <emojione-avocado/>
    <twemoji-coconut/>
  </div>
  <div>
    <span v-click class="mr-10">Brennstoff</span><br>
    <span v-click v-mark.underline.red="3">Vitamine</span>
  </div>
</div>

<v-click at=4>

### ungesättigte Fettsäuren

</v-click>

<div class="flex justify-between">
  <div v-click=4  class="flex space-x-2xl *:size-12">
    <img src="/icons/olive-oil.png"/>
    <openmoji-olive/>
    <emojione-v1-sunflower/>
    <twemoji-fish/>
  </div>
  <div v-click=5 class="mr-10 pt-4">Chemikalien</div>
</div>

</div>

<div>
  <img src="/images/kohle.webp" class="h-60"/>
  <img src="/images/putzmittel.avif" class="h-54 mt-4"/>
</div>
</div>

---

<br><br>

## Das Problem mit den

# **Kohlenhydraten / Zucker**

---
layout: image-right
image: /images/papier.avif
---

## Kohlenhydrate

<div class="*:size-12 *:m-2" >
  <emojione-baguette-bread />
  <emojione-croissant />
  <emojione-pancakes />
  <noto-cooked-rice />
  <emojione-spaghetti />
  <emojione-hamburger />
  <emojione-pizza />
  <twemoji-banana />
  <streamline-emojis-candy />
  <img src="/icons/ketchup.png" class="inline-block align-top"/>
  <noto-beverage-box />
  <img src="/icons/cola.png" class="inline-block align-top"/>
</div>

<br>
<br>

### Brennstoff

#### Schnell verfügbare Energie

#### Speicherbar

<v-clicks depth="2">

- Leber (kurzfristige Energie ca 90 Min)
- Fett (langfristig)

</v-clicks>

---

<br><br>

## Das Problem mit den

# **Gewohnheiten**
