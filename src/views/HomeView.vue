<template>
  <div class="home">
    <Navbar />
    <div class="container">
      <div class="mt-3 mb-5">

           <!-- Carousel -->
      <b-carousel
      id="carousel-1"
      v-model="slide"
      :interval="4000"
      controls
      indicators
      img-width="1024"
      img-height="480"
      style="text-shadow: 1px 1px 2px #333;"
      @sliding-start="onSlideStart"
      @sliding-end="onSlideEnd">
      <!-- Text slides with image -->
      <b-carousel-slide>
        <template #img>
          <img
            class="d-block img-fluid w-100"
            src="assets/images/9.jpg"
            alt="image slot"
          >
        </template>
      </b-carousel-slide>

      <!-- Slides with custom text -->
      <b-carousel-slide>
        <template #img>
          <img
            class="d-block img-fluid w-100"
            src="assets/images/b1.png"
            alt="image slot"
          >
        </template>
      </b-carousel-slide>

      <!-- Slides with image only -->
      <b-carousel-slide>
        <template #img>
          <img
            class="d-block img-fluid w-100"
            src="assets/images/b2.png"
            alt="image slot"
          >
        </template>
      </b-carousel-slide>

      
    </b-carousel>
        </div>

      <div class="row mt-5 mb-3">
        <div class="col">
          <h2 class="text-center">
            
            <strong>Best Foods Menu</strong>
          </h2>
        </div>
      </div>

      <div class="row mb-5">
        <div class="col-md-4 mt-2" v-for="product in products" :key="product._id">
          <CardProduct :product="product"/>
         
        </div>
      </div>
      <div class="col mb-5 text-center">
          <router-link to="/foods" class="btn btn-primary" >
            <b-icon-eye></b-icon-eye>Load More Menu
          </router-link>
        </div>
      
        <Hero />

        <b-card class="mt-5 mb-5"
    overlay
    img-src="https://picsum.photos/900/250/?image=3"
    img-alt="Card Image"
    text-variant="white"
  >
  <h1 class="text-center"><strong>Contact Email CAFE MOON</strong></h1>
  <div class="text-center mr-5 ml-5">
    <b-form-input class="my-4 mb-4 text-center" size="lg" v-model="text" placeholder="Send your feedback about us"></b-form-input>
    <b-button size="lg" class=" bg-primary" to="feedback">SUBMIT</b-button>
  </div>
  </b-card>


    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navbar from "@/components/Navbar.vue";
import Hero from "@/components/Hero.vue";
import CardProduct from "@/components/CardProduct.vue"
import axios from "axios";

export default {
  name: "HomeCafe",
  components: {
    Navbar,
    Hero,
    CardProduct
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProducts(data) {
      this.products = data;
    },
  },
  mounted() {
    axios
      .get("https://testapi-pink.vercel.app/products/12/b")
      .then((response) => this.setProducts(response.data))
      .catch((error) => console.log(error))
},
};

</script>