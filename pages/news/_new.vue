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
        <div v-if="number==counter">
          <button><a :href="'/news/' + number"><b>{{ number }}</b></a></button>
        </div>
        <div v-else>
          <button><a :href="'/news/' + number">{{ number }}</a></button>
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

let pageAmount = 2
export default {
    components: {
    Topmenu
  },
  asyncData: async function({$axios, params}) {
    try{
    const response = await $axios.get(`http://185.158.153.91:1380/news?_limit=${pageAmount}&_start=${(params.new - 1)*pageAmount}`)
    const ba = await $axios.get(`http://185.158.153.91:1380/news/count`)
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
  } 
}
</script>

<style>
  #parent_buttom{
    display: flex
  }
</style>

