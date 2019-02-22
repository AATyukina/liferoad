<template>
  <div>
    <topmenu />
    <div class="cont">
      <h1>{{ university.Название }}</h1>
      <dl class="dl-horizontal">
        <dt> Код: </dt>
        <dd> {{ university.Код }} </dd>
        <dt> Описание: </dt>
        <dd> {{ university.Описание }} </dd>
        <dt> E-mail: </dt>
        <dd>  {{ university.Email }} </dd>
        <dt> Телефон: </dt>
        <dd> {{ university.Телефон }} </dd>
        <dt> Специальности: </dt>
        <dd> 
          <ul 
            v-for="speciality in university.специальность"
            :key="speciality">
            <li >
              <a :href="'/specialities/' + speciality.id"> {{ speciality.Название }} </a>
            </li>
          </ul>
        </dd>
      </dl>
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
    const response = await $axios.get(constants.baseUrl + '/universities?%D0%9A%D0%BE%D0%B4='+ params.id)
    return {
       university: response.data[0]
    }
  }
}
</script>

<style>
 .cont{
   padding: 10px;
 }
</style>
