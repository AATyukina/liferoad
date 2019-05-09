<template>
  <div class="total">
    <topmenu />
    <div 
      v-if="flag"
      class="new_container">
      <div class="new_name">
        <h3>{{ n.Название }}</h3>
      </div>
      <div class="new_description">
        <p>{{ n.Полно }}</p>
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

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat|Roboto+Slab');
.total{
  width: 2000px;
  margin: 0 auto;
}
.new_container{
  margin-left: 117px;
    margin-top: 46px;
    margin-right: 117px;
    margin-bottom: 80px;
}
.new_name{
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
.new_description{
  margin-top: 40px;
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 15px;
  line-height: 29px;

  color: #1D262D;
}
</style>
