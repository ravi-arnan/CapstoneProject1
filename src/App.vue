<template>
  <section
    class="bg-gradient-to-b from-linearBlue/40 via-white pb-10 to-linearBlue/40"
  >
    <Header></Header>
    <Hero :hero-images="heroImages"></Hero>
  </section>
  <section>
    <Mission :about-image="aboutImage"></Mission>

    <FoodList :food-images="foodImages"></FoodList>

    <Mountain :successful-adventure="successfulAdventure"></Mountain>
  </section>
  <section
    class="bg-gradient-to-b from-linearBlue/40 via-white to-linearBlue/40"
  >
    <Accordion></Accordion>
    <Footer></Footer>
  </section>
</template>

<script setup>
import Header from "./components/HeaderPage.vue";
import Hero from "./components/HeroPage.vue";
import Mission from "./components/MissionPage.vue";
import FoodList from "./components/FoodList.vue";
import community from "./assets/community.png";
import Footer from "./components/Footer.vue";
import Accordion from "./components/Accordion.vue";
import Mountain from "./components/MountainPage.vue";
import MountainImg from "./assets/mountain.png";
import heroImage from "./assets/adventures.png";
import logo1 from "./assets/logo1.png";
import logo2 from "./assets/logo2.png";
import logo3 from "./assets/logo3.png";
import logo4 from "./assets/logo4.png";
import food1 from "./assets/food1.png";
import food2 from "./assets/food2.png";
import food3 from "./assets/food3.png";
import food4 from "./assets/food4.png";
import food5 from "./assets/food5.png";
import food6 from "./assets/food6.png";
import food7 from "./assets/food7.png";
import food8 from "./assets/food8.png";
const heroImages = [
  {
    src: heroImage,
    alt: "hero image",
  },
  {
    src: logo1,
    alt: "logo 1",
  },
  {
    src: logo2,
    alt: "logo 2",
  },
  {
    src: logo3,
    alt: "logo 3",
  },
  {
    src: logo4,
    alt: "logo 4",
  },
];
const aboutImage = [
  {
    src: community,
    alt: "community image",
    titleHeader: "OUR MISSION FOR ADVENTURE",
    title: " Choose and Stock Your Next Adventure",
    desc: "Explore our delicious food and drink options at Blox Food. We have the provisions you need to conquer any journey.",
    communityHeader: "BLOX FOOD COMMUNITY",
    communityTitle: "Connect with Blox Food adventurers across the globe!",
    communityDesc:
      "Blox Food Community: fueling journeys, fostering connections. Adventure enthusiasts, diverse palates, shared excitement.",
    countOne: 2000,
    countOneDetail: "Adventurers",
    countTwo: 2500,
    countTwoDetail: "Meals Served",
    countThree: 5000,
    countThreeDetail: "Bobux Spent",
  },
];
const foodImages = [
  {
    src: food1,
    alt: "rich",
    name: "Bloxy Cola",
    price: "200 Bobux",
  },
  {
    src: food2,
    alt: "rich",
    name: "Chezburger",
    price: "500 Bobux",
  },
  {
    src: food8,
    alt: "broke",
    name: "Space Sandwich",
    price: "50 Bobux",
  },
  {
    src: food5,
    alt: "broke",
    name: "Hot Dog",
    price: "60 Bobux",
  },
  {
    src: food3,
    alt: "rich",
    name: "PIZZA!",
    price: "300 Bobux",
  },
  {
    src: food4,
    alt: "rich",
    name: "Mm Chavez",
    price: "500 Bobux",
  },

  {
    src: food6,
    alt: "broke",
    name: "Witches Brew",
    price: "50 Bobux",
  },
  {
    src: food7,
    alt: "broke",
    name: "Beans",
    price: "30 Bobux",
  },
];
const successfulAdventure = [
  {
    src: MountainImg,
    alt: "mountain img",
    titleHead: "SUCCESSFUL ADVENTURE",
    title: "Pre-Adventure Supplies Ready Set Go",
    desc: "Pre-Adventure Supplies Ready Set Go ensures you're perfectly prepared. We make getting your food and drink effortless, so your adventure can truly begin.",
    button: "Buy now",
  },
];
</script>
