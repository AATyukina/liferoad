<template>
  <div>
    <div>
      <a href="../">Главная страница</a>
    </div>
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
</template>

<script>
export default {
  asyncData: async function({$axios}) {
    const response = await $axios.get('http://185.158.153.91:1380/specialities')
    return {
      specialities: response.data
    }
  }
  // $axios.get('http://185.158.153.91:1380/specialities')
  //     .then(function (response) {
  //       return {
  //         specialities: response.data
  //       }
  //     })
  //     .catch(function (error) {
  //       console.log(error); 
  //     });
  // }
  // выводит надпись "Специальности", а дальше не отображает их список
}
</script>