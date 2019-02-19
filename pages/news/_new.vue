<template>
  <div>
    <topmenu />
    <h3> Новости </h3>
    <div 
      v-for="n in news"
      :key="n">
      <div>
        <a :href="'details/' + n.id">{{ n.Название }}</a>
        <p>{{ n.Кратко }}</p>
      </div>
    </div>
    <div
      v-for="number in bottom_amount"
      :key="number">
      <div v-if="number==counter">
        <button><a :href="'/news/' + number"><b>{{ number }}</b></a></button>
      </div>
      <div v-else>
        <button><a :href="'/news/' + number">{{ number }}</a></button>
      </div>
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
    const response = await $axios.get(`http://185.158.153.91:1380/news?_limit=${pageAmount}&_start=${(params.new - 1)*pageAmount}`)
    const ba = await $axios.get(`http://185.158.153.91:1380/news`)
    const all_bottom = Math.floor( ba.data.length / pageAmount )
    var bottom_amount = ba.data.length%pageAmount>0?all_bottom+1:all_bottom
    return {
       bottom_amount,
       news: response.data,
       counter: params.new
    }
  }  
}
</script>
