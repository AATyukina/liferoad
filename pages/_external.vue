<template>
  <div class="container">
    <div v-if="flag">
      hello, do you want some data?
    </div>
    <div v-else> 
      <h2>Oops! Page not found! But don't worry! <br> Error code  {{ code }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  asyncData: async function({$axios}) {
    try{
      const response = await $axios.get('http://185.158.153.91:1380/university')
        return {
           data: response.data,
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
