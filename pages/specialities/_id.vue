<template>
  <div class="total">
    <topmenu />
    <h1> {{ speciality.Название }} </h1>
    <div v-html="$md.render(speciality.Полное)" />
    <div>
      <div 
        v-for="(item, index) in speciality.профессии"
        :key="item"
        class="prof_container">
        <a @click="activeItem = index">{{ item.Название }}</a>
      </div>
      <div v-html="speciality.профессии[activeItem].Видео" />
      <div v-html="$md.render(speciality.профессии[activeItem].Описание)" />
    </div>
    <div>
      <div> Университеты: </div>
      <ul 
        v-for="university in speciality.вузы"
        :key="university">
        <li >
          <a :href="'/universities/' + university.Код"> {{ university.Название }} </a>
        </li>
      </ul> 
    </div>
    <Downfooter />
  </div>
</template>

<script>
import Topmenu from '~/components/Topmenu.vue';
import constants from "assets/constants";
import Downfooter  from '~/components/Downfooter.vue'
export default {

  components: {
    Topmenu,
    Downfooter
  },

  asyncData: async function({$axios, params}) {
    const response = await $axios.get(constants.baseUrl + '/specialities/'+ params.id)
    return {
       speciality: response.data,
       activeItem: 0
    }
  },
  head() {
    return{
      title: 'Специальность: ' + this.speciality.Название + '. Проект "Путевка в жизнь"',
      meta: [
        {hid: 'description', 'name':'description', 'content': 'Профориентационный проект "Путевка в жизнь" для абитуриентов Нижегородской области и их родителей. Специальность: ' + this.speciality.Название}
      ]
    }
  }
}
</script>

<style>
.total{
  width: 2000px;
  margin: 0 auto;
}
.prof_container{
  display: inline-flex; 
  justify-content: flex-start;
  margin-right: 20px;
}
</style>
