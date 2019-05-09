<template>
  <div class="total">
    <topmenu />
    <div class="un_container">
      <h3 class="un_title"> Университеты </h3>
      <div
        v-for="university in universities"
        :key="university"
        class="un_unit">
        <a :href="university.Код"> {{ university.Название }} </a>
      </div>
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

  asyncData: async function({$axios}) {
    const response = await $axios.get(constants.baseUrl + '/universities')
    return {
      universities: response.data
    }
  },
    head() {
    return{
      title: 'Университеты. Проект "Путевка в жизнь"',
      meta: [
        {hid: 'description', 'name':'description', 'content': 'Профориентационный проект "Путевка в жизнь" для абитуриентов Нижегородской области и их родителей. Университеты'}
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
.un_container{
  margin-left: 117px;
    margin-top: 46px;
    margin-right: 117px;
    margin-bottom: 80px;
}
.un_title{
width: 238px;
    height: 32px;

   font-family: 'Roboto Slab', serif;
  font-style: normal;
  font-weight: bold;
  line-height: normal;
  font-size: 38px;
  text-transform: uppercase;
  color: #5d3dc6;
  margin-bottom: 63px;
}
.un_unit{
  margin-top: 30px;
  height: 50px;
width: auto;
  box-shadow: 0px 1px 4px #ebe8e8;
  border-radius: 1px;
}
.un_unit a{
  width: 380px;
  height: 32px;

  font-family: 'Roboto Slab', serif;
  font-style: normal;
  font-size: 24px;
  line-height: 32px;
  text-transform: uppercase;

  color: #1D262D;
}
</style>
