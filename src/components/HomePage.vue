<template>
  <v-container fluid class="pa-0">
    <v-row>
      <v-col cols="12" class="d-flex flex-wrap pa-0">
        <v-col cols="12" md="7" class="left pa-0">
          <div class="nav d-flex justify-space-between d-md-none mt-10 ml-10">
            <div class="icon1">
              <v-icon @click="dialog = true">mdi-menu</v-icon>
            </div>
            <!-- Dialog Box -->
            <v-dialog :scrim="false" v-model="dialog" width="100vw">
              <v-card class="dialog-card d-flex d-md-none">
                <v-card-text class="d-flex flex-column justify-center">
                  <!-- Navigation Links -->
                  <nav class="link-container link2 d-flex align-center">
                    <a href="#">
                      <div class="close d-flex align-center">
                        <img
                          @click="dialog = false"
                          src="/src/assets/icon-close.svg"
                          alt=""
                        />
                      </div>
                    </a>
                    <div class="link22 ml-12">
                      <a href="#" class="link">home</a>
                      <a href="#" class="link">shop</a>
                      <a href="#" class="link">about</a>
                      <a href="#" class="link">contact</a>
                    </div>
                  </nav>
                </v-card-text>
              </v-card>
            </v-dialog>
            <div class="logo2">
              <img src="/src/assets/logo.svg" alt="" />
            </div>
          </div>
          <div class="nav d-none d-md-flex align-center mt-15 ml-14">
            <div class="logo">
              <img src="/src/assets/logo.svg" alt="" />
            </div>
            <div class="links d-flex align-center ml-9">
              <div class="link"><a href="">home</a></div>
              <div class="link"><a href="">shop</a></div>
              <div class="link"><a href="">about</a></div>
              <div class="link"><a href="">contact</a></div>
            </div>
          </div>

          <v-carousel
            :show-arrows="false"
            v-model="currentSlide"
            hide-delimiters
            class="carousel-container d-none d-md-block"
          >
            <v-carousel-item
              class=""
              v-for="(image, index) in images"
              :key="index"
            >
              <div
                class="carousel-image pa-0"
                :style="{ backgroundImage: `url(${image})` }"
              ></div>
            </v-carousel-item>
          </v-carousel>

          <!-- MD Screen -->
          <v-carousel
            :show-arrows="false"
            v-model="currentSlide"
            hide-delimiters
            class="carousel-container d-block d-md-none"
          >
            <v-carousel-item
              class=""
              v-for="(image, index) in images2"
              :key="index"
            >
              <div
                class="carousel-image pa-0"
                :style="{ backgroundImage: `url(${image})` }"
              ></div>
            </v-carousel-item>
            <div class="slider-buttons2 d-flex d-md-none align-center">
              <v-btn
                icon
                class="arrow-btn px-9 py-9 d-flex"
                size="large"
                rounded="0"
                elevation="0"
                @click="prevSlide"
              >
                <img src="/src/assets/icon-angle-left.svg" alt="" />
              </v-btn>
              <v-btn
                icon
                class="arrow-btn px-9 py-9 d-flex"
                size="large"
                rounded="0"
                elevation="0"
                @click="nextSlide"
              >
                <img src="/src/assets/icon-angle-right.svg" alt="" />
              </v-btn>
            </div>
          </v-carousel>
        </v-col>
        <v-col
          cols="12"
          md="5"
          class="pa-0 d-flex flex-column justify-space-between position-relative right1"
        >
          <div class="text-content text-center">
            <h1 class="heading">{{ currentHeading }}</h1>
            <p class="para mt-5">{{ currentParagraph }}</p>
            <div class="subheading d-flex align-center mt-5 pa-0">
              <div class="text2 mr-5 d-flex align-center pa-0">
                SHOP NOW
                <v-icon
                  class="right-arrow d-block ml-2"
                  icon="mdi-arrow-right-thin"
                  size="x-large"
                ></v-icon>
              </div>
            </div>
          </div>

          <div class="slider-buttons d-none d-md-flex align-center">
            <v-btn
              icon
              class="arrow-btn px-9 py-9 d-flex"
              size="large"
              rounded="0"
              elevation="0"
              @click="prevSlide"
            >
              <img src="/src/assets/icon-angle-left.svg" alt="" />
            </v-btn>
            <v-btn
              icon
              class="arrow-btn px-9 py-9 d-flex"
              size="large"
              rounded="0"
              elevation="0"
              @click="nextSlide"
            >
              <img src="/src/assets/icon-angle-right.svg" alt="" />
            </v-btn>
          </div>
        </v-col>
      </v-col>

      <v-col cols="12" class="outer-col d-flex flex-wrap pa-0">
        <!-- First partition with 30vw -->
        <div class="d-inline-block first-partition"></div>

        <!-- Second partition with 40vw -->
        <div class="d-inline-block second-partition">
          <div class="heading2">ABOUT OUR FURNITURE</div>
          <div class="para2 mt-2">
            Our multifunctional collection blends design and function to suit
            your individual taste. Make each room unique, or pick a cohesive
            theme that best express your interests and what inspires you. Find
            the furniture pieces you need, from traditional to contemporary
            styles or anything in between. Product specialists are available to
            help you create your dream space.
          </div>
        </div>

        <!-- Third partition with 30vw -->
        <div class="d-inline-block third-partition"></div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref, computed } from "vue";

const dialog = ref(false);
// Images for the carousel
const images = [
  "/src/assets/desktop-image-hero-1.jpg",
  "/src/assets/desktop-image-hero-2.jpg",
  "/src/assets/desktop-image-hero-3.jpg",
];

const images2 = [
  "/src/assets/mobile-image-hero-1.jpg",
  "/src/assets/mobile-image-hero-2.jpg",
  "/src/assets/mobile-image-hero-3.jpg",
];

// Headings and paragraphs data
const headings = [
  "Discover innovative ways to decorate",
  "We are available all across the globe",
  "Manufactured with the best materials",
];
const paragraphs = [
  "We provide unmatched quality, comfort, and style for property owners across the country. Our experts combine form and function in bringing your vision to life. Create a room in your own style with our collection and make your property a reflection of you and what you love.",
  "With stores all over the world, it's easy for you to find furniture for your home or place of business. Locally, we're in most major cities throughout the country. Find the branch nearest you using our store locator. Any questions? Don't hesitate to contact us today.",
  "Our modern furniture store provide a high level of quality. Our company has invested in advanced technology to ensure that every product is made as perfect and as consistent as possible. With three decades of experience in this industry, we understand what customers want for their home and office.",
];

const currentSlide = ref(0);

// Compute the current heading and paragraph based on the current slide index
const currentHeading = computed(() => headings[currentSlide.value]);
const currentParagraph = computed(() => paragraphs[currentSlide.value]);

// Slide control functions
function nextSlide() {
  currentSlide.value = (currentSlide.value + 1) % headings.length;
}

function prevSlide() {
  currentSlide.value =
    (currentSlide.value - 1 + headings.length) % headings.length;
}
</script>

<style scoped>
@font-face {
  font-family: f1;
  src: url(/src/assets/LeagueSpartan-Regular.ttf);
}
@font-face {
  font-family: f2;
  src: url(/src/assets/LeagueSpartan-Medium.ttf);
}
@font-face {
  font-family: f3;
  src: url(/src/assets/LeagueSpartan-Bold.ttf);
}
.text2 {
  font-family: f2;
  letter-spacing: 10px;
  font-size: 14px;
  color: hsl(0, 0%, 11%);
}
.text2:hover {
  color: hsl(0, 0%, 68%);
  cursor: pointer;
  transition: 0.1s ease-in;
}
.right-arrow {
  position: relative;
  top: -2px;
}
.upper {
  background-color: #a83333;
}
.heading {
  font-family: f2;
  letter-spacing: 0px;
  text-align: left;
  font-size: 40px;
  color: hsl(0, 0%, 5%);
  line-height: 40px;
}
.para {
  font-family: f2;
  word-spacing: -0.5px;
  color: hsl(0, 0%, 63%);
  font-size: 14px;
  text-align: left;
}
.right1 {
  color: black;
  background-color: #fff;
}
.image-carousel {
  height: 400px; /* Adjust height as needed */
  position: relative;
}

/* Ensure background images are styled properly */
.carousel-image {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

.text-content {
  margin-top: 105px;
  padding-left: 83.5px;
  padding-right: 83.5px;
  margin-bottom: 125px;
}

.slider-buttons {
  position: absolute;
  bottom: 0px;
  left: 0px;
}
.slider-buttons2 {
  position: absolute;
  bottom: 0px;
  right: 0px;
}

.arrow-btn {
  background-color: rgb(0, 0, 0);
  width: 40px;
  height: 40px;
}
.arrow-btn:hover {
  background-color: hsl(0, 0%, 27%);
}
.nav {
  position: absolute;
  z-index: 100;
}
.link a {
  margin-right: 15px;
  margin-left: 15px;
  text-decoration: none;
  color: white;
  font-size: 12px;
  position: relative;
}
.link a::after {
  content: "";
  position: absolute;
  left: 50%; /* Start in the middle to allow for a smooth transition */
  bottom: -8px; /* Adjust the position slightly below the text */
  width: 0;
  height: 1.5px; /* Height of the line */
  background-color: white;
  transition: all 0.3s ease;
  transform: translateX(-50%); /* Centers the line */
}

.link a:hover::after {
  width: 15px; /* Width of the line on hover */
}
.link2 a {
  margin-right: 15px;
  margin-left: 15px;
  text-decoration: none;
  color: hsl(0, 0%, 0%);
  font-size: 14px;
  position: relative;
  font-family: f3;
}
.link22 a::after {
  content: "";
  position: absolute;
  left: 50%; /* Start in the middle to allow for a smooth transition */
  bottom: -8px; /* Adjust the position slightly below the text */
  width: 0;
  height: 1.5px; /* Height of the line */
  background-color: rgb(0, 0, 0);
  transition: all 0.3s ease;
  transform: translateX(-50%); /* Centers the line */
}

.link22 a:hover::after {
  width: 15px; /* Width of the line on hover */
}
.logo {
  position: relative;
  top: 2.7px;
}
.logo2 {
  position: relative;
  top: 3px;
  margin-left: 40.5vw;
  margin-right: 50vw;
}
.mid {
  background-color: #fff;
}
.heading2 {
  color: hsl(0, 0%, 5%);
  font-size: 15px;
  font-family: f3;
  letter-spacing: 5px;
}
.para2 {
  font-family: f2;
  word-spacing: -0.5px;
  color: hsl(0, 0%, 63%);
  font-size: 14px;
  text-align: left;
}
/* Optional styling for different partitions */
.first-partition {
  width: 30vw;
  background-color: #f5f5f5;
  background-image: url("/src/assets/image-about-dark.jpg"); /* Ensure correct path */
  background-size: cover; /* Makes the image cover the entire partition */
  background-position: center; /* Centers the image within the div */
  background-repeat: no-repeat; /* Prevents the image from tiling */
}
.second-partition {
  width: 40vw;
  background-color: #ffffff;
  padding-left: 43px;
  padding-right: 43px;
  padding-top: 59px;
  padding-bottom: 59px;
}
.third-partition {
  width: 30vw;
  background-image: url("/src/assets/image-about-light.jpg"); /* Ensure correct path */
  background-size: cover; /* Makes the image cover the entire partition */
  background-position: center; /* Centers the image within the div */
  background-repeat: no-repeat; /* Prevents the image from tiling */
}
.dialog-card {
  height: 20vh;
  width: 100vw;
  position: fixed;
  top: -290px;
  left: -25px;
  background-color: #fff;
}

/* MEDIA QUERIES */
@media screen and (min-width: 959.5px) and (max-width: 1199.5px) {
  .text-content {
    padding-left: 35px;
    padding-right: 35px;
  }
}
@media screen and (max-width: 959.5px) {
  .first-partition {
    width: 100vw;
    height: 100%;
  }
  .second-partition {
    width: 100vw;
    padding-left: 43px;
    padding-right: 43px;
    padding-top: 40px;
    padding-bottom: 40px;
  }
  .third-partition {
    width: 100vw;
    height: 100%;
  }
  .text-content {
    margin-top: 65px;
    padding-left: 83.5px;
    padding-right: 83.5px;
    margin-bottom: 70px;
  }
  .text-content {
    padding-left: 50px;
    padding-right: 50px;
  }
}
@media screen and (max-width: 599.5px) {
  .logo2 {
    margin-left: 32vw;
  }
}
</style>
