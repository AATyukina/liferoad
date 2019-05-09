<template>
  <div class="total">
    <topmenu />
    <div 
      v-if="flag"
      class="sp_container">
      <h3 class="sp_title"> Специальности </h3>
      <div
        v-for="speciality in specialities"
        :key="speciality"
        class="sp_unit">
        <a :href="speciality.id"> {{ speciality.Название }} </a>
      </div>
    </div>
    <div v-else> 
      <h2>Oops! Page not found! But don't worry! <br> Error code  {{ code }}</h2>
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
  asyncData: async function({$axios}) {
    try{
      const response = await $axios.get(constants.baseUrl + '/specialities')
        return {
           specialities: response.data,
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
      title: 'Специальности. Проект "Путевка в жизнь"',
      meta: [
        {hid: 'description', 'name':'description', 'content': 'Профориентационный проект "Путевка в жизнь" для абитуриентов Нижегородской области и их родителей. Специальности.'}
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
.sp_container{
  margin-left: 117px;
    margin-top: 46px;
    margin-right: 117px;
    margin-bottom: 80px;
}
.sp_title{
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
.sp_unit{
  margin-top: 30px;
  height: 50px;
width: auto;
  box-shadow: 0px 1px 4px #ebe8e8;
  border-radius: 1px;
}
.sp_unit a{
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
