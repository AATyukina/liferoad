<template>
  <div>
    hello
  </div>
</template>

<script>
export default {
    asyncData: async function({$axios, data}) {
      $axios.get('http://185.158.153.91:1380/specialities')
      .then(function (response) {
        return {
          specialities: response.data
        }
      })
      .catch(function (error) {
        console.log(error); 
      });
  }
   
}
</script>
