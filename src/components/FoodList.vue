<template>
  <div id="food-lists">
    <div class="container mx-auto px-5 lg:px-8 pb-10">
      <div class="mb-7" id="foodlist-title">
        <h5
          class="text-lightBlue tracking-wider mb-3 md:text-base lg:text-lg font-semibold text-sm font-Sawa"
        >
          OUR AMAZING MENU
        </h5>
        <h1
          class="text-secondBlack text-2xl font-semibold md:text-3xl leading-normal lg:leading-normal lg:max-w-md lg:text-4xl font-Inter mb-7"
        >
          Fuel your next adventure!
        </h1>
        <p
          class="text-secondGray font-Sawa text-base md:max-w-lg lg:text-xl md:text-lg mb-10"
        >
          Dive into our delicious selection of food and drinks. Your journey starts with BloxFood!
        </p>
      </div>
      <div>
        <div
          id="foodlist-filter"
          class="grid grid-cols-3 items-center max-w-sm ml-auto mb-16"
        >
          <div
            v-for="(category, index) in ['RICH', 'BROKE', 'ALL']"
            :key="index"
            @click="handleCategoryClick(category)"
            :class="{
              'border-[1px] cursor-pointer border-paleBlue/75 hover:bg-paleBlue text-paleBlue duration-200 ease-in-out group py-2':
                selectedCategory !== category,
              'border-[1px] cursor-pointer bg-paleBlue text-white duration-200 ease-in-out group py-2':
                selectedCategory === category,
            }"
          >
            <p
              class="text-base font-Inter font-medium text-center group-hover:text-white duration-200 ease-in-out"
            >
              {{ category }}
            </p>
          </div>
        </div>
        <div
          v-auto-animate="{ duration: 600 }"
          class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-10 items-center"
        >
          <div v-for="(food, index) in filteredFoodImages" :key="index">
            <div class="relative group" id="foodlist-img">
              <img
                :src="food.src"
                :alt="food.alt"
                class="mb-4 mx-auto w-full rounded-lg"
              />
              <div
                class="absolute w-full h-full bg-gradient-to-b text-center group-hover:to-white/80 from-white/0 to-black/50 top-0"
              >
                <button
                  @click="buyFood"
                  class="px-14 text-base md:text-xl lg:text-base xl:text-xl lg:px-8 lg:mt-28 xl:mt-40 py-4 mt-44 md:mt-52 mb-20 xs:mb-28 lg:mb-12 xl:mb-24 bg-paleBlue opacity-0 group-hover:opacity-100 font-Sawa text-white rounded inline-block transition duration-300 ease-in-out hover:bg-slate-500"
                >
                  Buy now
                </button>
                <h1
                  class="text-2xl md:text-3xl font-Sawa text-white font-medium lg:text-xl group-hover:text-secondBlack duration-300 ease-in-out text-center"
                >
                  {{ food.price }}
                </h1>
              </div>
            </div>
            <div id="foodlist-detail">
              <h1
                class="text-2xl md:text-3xl lg:text-2xl font-Inter mb-1 font-semibold text-center text-secondBlack"
              >
                {{ food.name }}
              </h1>
              <p
                class="text-lg md:text-xl lg:text-lg font-Sawa font-semibold text-center"
              >
                {{ food.old }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref, computed, onMounted } from "vue";
import gsap from "gsap";
const props = defineProps({
  foodImages: {
    type: Array,
    required: true,
  },
});

onMounted(() => {
  gsap.from("#foodlist-title", {
    opacity: 0,
    y: 120,
    ease: "slow",
    scrollTrigger: {
      trigger: "#foodlist-title",
      once: true,
      start: "top 85%",
      scrub: 1,
      end: "+=180",
    },
  });
  gsap.from("#foodlist-filter", {
    opacity: 0,
    x: 120,
    duration: 1,
    ease: "slow",
    scrollTrigger: {
      trigger: "#foodlist-filter",
      once: true,
      start: "top 85%",
      scrub: 1,
      end: "+=180",
    },
  });
  gsap.from("#foodlist-img", {
    opacity: 0,
    x: 120,
    duration: 1,
    ease: "slow",
    scrollTrigger: {
      trigger: "#foodlist-img",
      once: true,
      start: "top center",
      scrub: 1,
      end: "+=200",
    },
  });
  gsap.from("#foodlist-detail", {
    opacity: 0,
    x: 120,
    duration: 1,
    ease: "slow",
    scrollTrigger: {
      trigger: "#foodlist-detail",
      once: true,
      start: "top 85%",
      scrub: 1,
      end: "+=150",
    },
  });
});

const selectedCategory = ref("ALL");
const filteredFoodImages = computed(() => {
  return props.foodImages.filter((food) => {
    if (selectedCategory.value === "ALL") {
      return true;
    } else if (selectedCategory.value === "RICH") {
      return food.alt && food.alt.toLowerCase().includes("rich");
    } else if (selectedCategory.value === "BROKE") {
      return food.alt && food.alt.toLowerCase().includes("broke");
    }
  });
});

const handleCategoryClick = (category) => {
  selectedCategory.value = category;
};
</script>
