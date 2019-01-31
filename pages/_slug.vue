<template>
  <div class="container">
    <div v-if="flag">
      <h3> {{ page.Название }} </h3>
      <p> {{ page.Текст }} </p>
    </div>
    <div v-else>
      <h3> Oops! Page not found! </h3>
    </div>
  </div>
</template>


<script>
export default {
  asyncData: async function({$axios, params}) {
    const response = await $axios.get('http://185.158.153.91:1380/pages')
    // return{
    //   pages: response.data,
    //   curPage: params.slug
    // }

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


    // flag_while = true
    // i = 0
    // while(flag_while){
    //   if (response.data[i].slug == data.slug){
    //     return{
    //       page: response.data[i], 
    //       flag: true
    //     }
    //     break
    //   }
    // }
  }
}
</script>
