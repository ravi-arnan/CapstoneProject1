<template>
  <div class="container mx-auto px-5 lg:px-8 pt-16 pb-24">
    <div class="text-center" id="accordion-title">
      <h5
        class="text-lightBlue tracking-wider mb-3 md:text-base lg:text-lg font-semibold text-sm font-Sawa"
      >
        Frequently Asked Questions
      </h5>
      <h1
        class="text-secondBlack text-2xl font-semibold md:text-3xl xl:max-w-md mx-auto xl:leading-relaxed lg:text-4xl font-Inter mb-5"
      >
        Purchase our high quality products!
      </h1>
      <p
        class="text-secondGray font-Sawa text-base md:max-w-md mx-auto lg:text-xl md:text-lg mb-8"
      >
        Fuel your adventure faster! We're here to help you get the provisions you need.
      </p>
    </div>
    <div
      class="grid grid-cols-1 max-w-4xl cursor-pointer mx-auto"
      id="accordions"
    >
      <div v-for="(item, index) in accordionItems" :key="index">
        <div
          class="p-5 border-[1px]"
          :class="{
            'border-paleBlue': item.show,
            'border-secondGray/40': !item.show,
          }"
          v-auto-animate
          @click="toggleAccordion(index)"
        >
          <div
            class="flex items-center justify-between"
            :class="{ 'mb-5': item.show, 'mb-0': !item.show }"
          >
            <div class="flex items-center gap-3">
              <span class="text-base md:text-lg text-paleBlue">&bull;</span>
              <p
                class="text-paleBlue md:text-lg text-base font-semibold font-Inter"
              >
                {{ item.title }}
              </p>
            </div>
            <i
              class="fa-solid"
              :class="{
                'fa-chevron-down text-paleBlue': !item.show,
                'fa-chevron-up text-secondGray/75': item.show,
              }"
            ></i>
          </div>
          <p
            class="text-base md:text-lg text-paleBlue font-Sawa"
            v-if="item.show"
          >
            {{ item.content }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";
const accordionItems = ref([
  {
    title: "How do I order?",
    content:
      "Just pick your items on our website and checkout. It's super easy!",
    show: false,
  },
  {
    title: "What kind of food do you have?",
    content:
      "We've got all sorts of snacks, drinks, and meals perfect for any adventure.",
    show: false,
  },
  {
    title: "How fast is delivery?",
    content:
      "We aim to get your order to you quickly so you're ready to go!",
    show: false,
  },
]);
const toggleAccordion = (index) => {
  accordionItems.value.forEach((item, i) => {
    item.show = i === index ? !item.show : false;
  });
};
onMounted(() => {
  gsap.from("#accordion-title", {
    opacity: 0,
    y: 120,
    duration: 1,
    ease: "slow",
    scrollTrigger: {
      trigger: "#accordion-title",
      once: true,
      start: "top center",
      scrub: 1,
      end: "+=100",
    },
  });
  gsap.from("#accordions", {
    opacity: 0,
    y: 60,
    duration: 1,
    ease: "slow",
    scrollTrigger: {
      trigger: "#accordions",
      once: true,
      start: "top center",
      scrub: 1,
      end: "+=40", //set the timing
    },
  });
});
</script>
