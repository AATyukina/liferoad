<template>
  <div>
    <topmenu />
    <div v-if="flag">
      <div>
        <h3> Специальности </h3>
      </div>
      <div>
        <ul 
          v-for="speciality in specialities"
          :key="speciality"
          class="list-unstyled">
          <li >
            <a :href="speciality.id"> {{ speciality.Название }} </a>
          </li>
        </ul> 
      </div>
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
  asyncData: async function({$axios}) {
    try{
      const response = await $axios.get('http://185.158.153.91:1380/specialities')
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
}
}
</script>