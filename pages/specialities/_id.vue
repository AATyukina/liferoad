<template>
  <div>
    <div>
      <a :href="/specialities/">Специальности</a>
    </div>
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
import axios from 'axios'

export default {
  asyncData: async function({$axios, params}) {
    const response = await axios.get('http://185.158.153.91:1380/specialities/'+ params.id)
    return {
       speciality: response.data
    }
  }
}
</script>