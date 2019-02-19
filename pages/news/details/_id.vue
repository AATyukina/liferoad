<template>
  <div>
    <topmenu />
    <div v-if="flag">
      <h3>{{ n.Название }}</h3>
      <p>{{ n.Полно }}</p>
    </div>
    <div v-else>
      <h2>Oops! Page not found! But don't worry! <br> Error code  {{ code }}</h2>
    </div>
  </div>
</template>

<script>
import Topmenu from '~/components/Topmenu.vue'
export default {
  components: {
    Topmenu
  },
  asyncData: async function({$axios, params}) {
    try{
      const response = await $axios.get(`http://185.158.153.91:1380/news?_id=${params.id}`)
        return {
           n: response.data[0],
           flag:true
      }
    }
    catch (error){
        return{
          flag: false, 
          code: error.response.status
        }
    }
}
}
</script>
