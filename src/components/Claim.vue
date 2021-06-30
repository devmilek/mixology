<template>
  <div class="claim">
    <h1>Mixology</h1>
    <p>Find best drinks for you</p>
    <input type="text" placeholder="Search" v-model="searchModel" @input="inputHandle">
    <div v-if="searchModel" class="search-results">
      <router-link :to="{name: 'Detail', params: {id: result.idDrink}}" class="box" v-for="result in results.slice(0, 5)" :key="result.idDrink">
        <img :src="result.strDrinkThumb" alt="">
        <p>{{ result.strDrink }}</p>
      </router-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Claim",
  data() {
    return{
      searchModel: '',
      results: [],
    }
  },
  methods: {
    inputHandle() {
      axios.get(`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${this.searchModel}`).then((response) => {
        this.results = response.data.drinks;
      });
    }
  }
}
</script>

<style scoped lang="scss">
.claim {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 80px;
  h1 {
    font-size: 50px;
  }
  p {
    font-size: 24px;
  }
  input {
    border: none;
    outline: none;
    border-bottom: 1px solid black;
    background: none;
    width: 320px;
    text-align: center;
    font-size: 20px;
    font-weight: 400;
    padding-bottom:6px;
    margin-top: 50px;
    transition: 0.5s all ease;
    &:focus {
      box-shadow: 0 18px 18px rgba(0, 0, 0, 0.1);
    }
  }
  .search-results {
    position: absolute;
    top: 251px;
    width: 320px;
    .box {
      height: 56px;
      display: flex;
      background: white;
      padding: 8px;
      align-items: center;
      border-bottom: 1px solid rgba(0, 0, 0, 0.1);
      cursor: pointer;
      img{
        height: 100%;
        margin-right: 20px;
      }
      p {
        font-size: 14px;
        font-weight: 600;
        opacity: 0.8;
      }
    }
  }
}
</style>
