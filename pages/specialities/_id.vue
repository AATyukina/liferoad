<template>
  <div>
    <topmenu />
    <h1> {{ speciality.Название }} </h1>
    <dl class="dl-horizontal">
      <dt> Описание: </dt>
      <dd> {{ speciality.Описание }} </dd>
      <dt> Университеты: </dt>
      <dd> 
        <ul 
          v-for="university in speciality.вузы"
          :key="university">
          <li >
            <a :href="'/universities/' + university.Код"> {{ university.Название }} </a>
          </li>
        </ul> 
      </dd>
    </dl>
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
    const response = await $axios.get(constants.baseUrl + '/specialities/'+ params.id)
    return {
       speciality: response.data
    }
  }
}
</script>