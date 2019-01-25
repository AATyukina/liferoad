<template>
  <div>
    <div>
      <a href="../">Главная страница</a>
    </div>
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
export default {
  asyncData: async function({$axios}) {
    const response = await $axios.get('http://185.158.153.91:1380/universities')
    return {
      universities: response.data
    }
  }
}
</script>