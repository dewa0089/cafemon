<template>
  <div>
 <Navbar />
 <div class="container">
   <div class="row mt-4">
     <div class="col text-center">
       <h2>
         List
         <strong>Drink Menu</strong>
       </h2>
     </div>
   </div>

  

   <div class="row mb-4">
     <div class="col-md-4 mt-4" v-for="product in products" :key="product._id">
       <CardProduct :product="product" />
     </div>
   </div>
 </div>
</div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";

export default {
name: "FoodsCafe",
components: {
 Navbar,
 CardProduct,
},
data() {
 return {
   products: [],
   search: '',
 };
},
methods: {
 setProducts(data) {
   this.products = data;
 },
},
mounted() {
 axios
   .get("https://testapi-pink.vercel.app/products/2/k")
   .then((response) => this.setProducts(response.data))
   .catch((error) => console.log(error));
},
};
</script>

<style>

</style>