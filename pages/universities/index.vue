<template>
  <div>
    <topmenu />
    <div>
      <h3> Университеты </h3>
    </div>
    <div>
      <ul 
        v-for="university in universities"
        :key="university">
        <li >
          <a :href="university.Код"> {{ university.Название }} </a>
        </li>
      </ul> 
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
  }
}
</script>