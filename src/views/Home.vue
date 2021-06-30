<template>
  <div class="home">
    <Claim />
    <div class="grid-container">
      <div class="box" v-for="drink in drinks" :key="drink.idDrink">
        <img :src="drink.strDrinkThumb" alt="">
        <div class="row">
          <h2>{{ drink.strDrink }}</h2>
          <router-link :to="{name: 'Detail', params: {id: drink.idDrink} }">See more</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import Claim from "@/components/Claim";
import axios from 'axios';
import Claim from "@/components/Claim";
export default {
  name: 'Home',
  components: {Claim},
  data() {
    return {
      drinks: ''
    }
  },
  mounted() {
    axios.get(`https://www.thecocktaildb.com/api/json/v1/1/search.php?f=a`).then(response => (this.drinks = response.data.drinks));
  }
}
</script>

<style lang="scss" scoped>
  .grid-container {
    display: grid;
    padding: 50px 10%;
    grid-column-gap: 30px;
    grid-row-gap: 30px;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    .box {
      display: grid;
      img {
        width: 100%;
      }
      .row {
        background: white;
        display: flex;
        justify-content: space-between;
        padding: 10px 16px;
        align-items: center;
      }
    }
  }
</style>
