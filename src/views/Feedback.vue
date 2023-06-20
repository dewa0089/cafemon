<template>
  <div class="pesanan-sukses">
    <Navbar />
    <div class="container">
      <div class="row justify-content-center mt-5">
        <div class="col text-center">
          <img src="../assets/images/menunggu.png" width="300" />
          <h2><strong>Terima Kasih</strong></h2>
          <h4>Atas Masukan Anda<br> Selamat Berbelanja Di Cafe Moon</h4>
          <router-link to="/" class="btn btn-primary"><h5><Strong>Kembali Kehalaman Awal</Strong></h5></router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  name: "Feedback-cafe",
  components: {
    Navbar,
  },
};
</script>

<style>
</style>