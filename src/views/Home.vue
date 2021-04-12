<template>
  <div class="home">
    <!-- <hello-world/> -->
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <card-prod :products="products" />
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
// import HelloWorld from '../components/HelloWorld.vue';
import CardProd from '../components/CardProd.vue';


export default {
  name: "Home",
  components: {
    // HelloWorld
    CardProd
   
  },
  data() {
    return {
      products:[],
      user:{}
    };
  },
  methods: {
    getProd() {
      var url = "http://localhost:3000/products";
      axios
        .get(url)
        .then((res) => {
          this.products = res.data.found;
          this.user = res.data.user;
        })
        .then(() => {
          // this.activestory = this.tales[0];
        });
    },
  },
  created(){
    this.getProd()
  }
};
</script>
