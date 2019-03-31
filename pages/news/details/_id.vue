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
import constants from "assets/constants";

export default {
  components: {
    Topmenu
  },
  asyncData: async function({$axios, params}) {
    try{
      const response = await $axios.get(constants.baseUrl + `/news?_id=${params.id}`)
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
},
   head() {
    return{
      title: this.n.Название + '. Проект "Путевка в жизнь"',
      meta: [
        {hid: 'description', 'name':'description', 'content': 'Профориентационный проект "Путевка в жизнь" для абитуриентов Нижегородской области и их родителей. Страница: ' + this.n.Название}
      ]
    }
  }
}
</script>
