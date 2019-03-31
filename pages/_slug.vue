<template>
  <div>
    <topmenu />
    <div v-if="flag">
      <h3> {{ page.Название }} </h3>
      <p> {{ page.Текст }} </p>
    </div>
    <div v-else>
      <h3> Oops! Page not found! </h3>
    </div>
  </div>
</template>


<script>
import Topmenu from '~/components/Topmenu.vue';
import constants from "assets/constants";
export default {
  components: {
    Topmenu
  },
asyncData: async function({$axios, params}) {
    const response = await $axios.get(constants.baseUrl + '/pages')
    for (var i=0; i < response.data.length; i++){
      if (response.data[i].slug == params.slug){
        return {
          page: response.data[i],
          flag: true
        }
      }
    }
    return {
     flag: false
    }
  },
   head() {
    return{
      title: this.page.Название + '. Проект "Путевка в жизнь"',
      meta: [
        {hid: 'description', 'name':'description', 'content': 'Профориентационный проект "Путевка в жизнь" для абитуриентов Нижегородской области и их родителей. Страница: ' + this.page.Название}
      ]
    }
  }
}
</script>
