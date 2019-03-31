<template>
  <div>
    <topmenu />
    <h3> Новости </h3>
    <div v-if="flag">
      <div 
        v-for="n in news"
        :key="n">
        <div>
          <a :href="'details/' + n.id">{{ n.Название }}</a>
          <p>{{ n.Кратко }}</p>
        </div>
      </div>
      <div
        v-for="number in buttom_amount"
        :key="number">
        <div
          v-if="number==counter" 
          class="btm">
          <!-- <button><a :href="'/news/' + number"><b>{{ number }}</b></a></button> -->
          <a :href="'/news/' + number"><b>{{ number }}</b></a>
        </div>
        <div 
          v-else
          class="btm">
          <!-- <button><a :href="'/news/' + number">{{ number }}</a></button> -->
          <a :href="'/news/' + number">{{ number }}</a>
        </div>
      </div>
    </div>
    <div v-else> 
      <h2>Oops! Page not found! But don't worry! <br> Error code  {{ code }}</h2>
    </div>
  </div>
</template>

<script>
import Topmenu from '~/components/Topmenu.vue'
import constants from "assets/constants";

let pageAmount = 2
export default {
    components: {
    Topmenu
  },
  asyncData: async function({$axios, params}) {
    try{
    const response = await $axios.get(constants.baseUrl + `/news?_limit=${pageAmount}&_start=${(params.new - 1)*pageAmount}`)
    const ba = await $axios.get(constants.baseUrl + `/news/count`)
    var buttom_amount = Math.floor( ba.data / pageAmount ) + (ba.data%pageAmount>0?1:0)
    return {
       buttom_amount,
       news: response.data,
       counter: params.new,
       flag: true
    }
  }catch(error){
    return{
          flag: false, 
          code: error.response.status
        }
  } 
  },
     head() {
    return{
      title: 'Новости. Проект "Путевка в жизнь"',
      meta: [
        {hid: 'description', 'name':'description', 'content': 'Новости. Профориентационный проект "Путевка в жизнь" для абитуриентов Нижегородской области и их родителей.'}
      ]
    }
  }
}
</script>

<style>
  .btm{
    border: grey solid 0.5px;
    width: 2%;
    height: 2%;
    text-align: center;
    background-color: lightgray;
  }

</style>

