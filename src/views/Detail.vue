<template>
  <div class="detail">
    <div class="left">
      <h1>{{result.strDrink}}</h1>
      <h3>{{result.strCategory}}</h3>
      <h2>Instructions</h2>
      <p>{{result.strInstructions}}</p>
      <h2>Ingredients</h2>
      <div class="ingredients">
        <div class="rows" v-if="result.strIngredient1">
          <h2>{{result.strIngredient1}}</h2>
          <p>{{ result.strMeasure1 }}</p>
        </div>
        <div class="rows" v-if="result.strIngredient2">
          <h2>{{result.strIngredient2}}</h2>
          <p>{{ result.strMeasure2 }}</p>
        </div>
        <div class="rows" v-if="result.strIngredient3">
          <h2>{{result.strIngredient3}}</h2>
          <p>{{ result.strMeasure3 }}</p>
        </div>
        <div class="rows" v-if="result.strIngredient4">
          <h2>{{result.strIngredient4}}</h2>
          <p>{{ result.strMeasure4 }}</p>
        </div>
        <div class="rows" v-if="result.strIngredient5">
          <h2>{{result.strIngredient5}}</h2>
          <p>{{ result.strMeasure5 }}</p>
        </div>
        <div class="rows" v-if="result.strIngredient6">
          <h2>{{result.strIngredient6}}</h2>
          <p>{{ result.strMeasure6 }}</p>
        </div>
        <div class="rows" v-if="result.strIngredient7">
          <h2>{{result.strIngredient7}}</h2>
          <p>{{ result.strMeasure7 }}</p>
        </div>
        <div class="rows" v-if="result.strIngredient8">
          <h2>{{result.strIngredient8}}</h2>
          <p>{{ result.strMeasure8 }}</p>
        </div>
      </div>
    </div>
    <div class="right">
      <img :src="result.strDrinkThumb" alt="">
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "Detail",
  data() {
    return {
      result: '',
    }
  },
  mounted() {
    axios.get(`https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${this.$route.params.id}`).then(response => (this.result = response.data.drinks[0]))
  }
}
</script>

<style scoped lang="scss">
  .detail {
    display: grid;
    grid-template-columns: 1fr auto;
    .left{
      padding: 80px 40px;
      h1 {
        font-size: 50px;
      }
      h3 {
        font-weight: normal;
        font-size: 24px;
      }
      h2 {
        margin-top: 34px;
        margin-bottom: 20px;
        font-weight: 600;
        font-size: 24px;
      }
      .rows {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
        //height: 50px;
        h2 {
          font-weight: normal;
          font-size: 20px;
          margin-top: 0;
          margin-bottom: 0;
        }
        p {
          font-weight: 500;
          font-size: 14px;
          justify-self: end;
        }
      }
    }
    .right{
      height: 100vh;
      img {
        height: 100%;
      }
    }
  }
</style>
