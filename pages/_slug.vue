<template>
  <div class="total">
    <topmenu />
    <div 
      v-if="flag"
      class="slug_container">
      <div class="slug_name">
        <h3>{{ page.Название }}</h3>
      </div>
      <div class="slug_description">
        <p>{{ page.Текст }}</p>
      </div>
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

<style>
.total{
  width: 2000px;
  margin: 0 auto;
}
.slug_container{
  margin-left: 117px;
    margin-top: 46px;
    margin-right: 117px;
    margin-bottom: 80px;
}
.slug_name{
    width: 380px;
  height: 32px;

  font-family: 'Roboto Slab', serif;
  font-style: normal;
  font-weight: bold;
  font-size: 24px;
  line-height: 32px;
  text-transform: uppercase;

  color: #1D262D;
}
.slug_description{
  margin-top: 40px;
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 15px;
  line-height: 29px;

  color: #1D262D;
}
</style>

