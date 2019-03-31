<template>
  <div class="wrapper">
    <topmenu />
    <middle />
    <div id="spec_group">
      <div class="spec_group_text"><a>IT</a></div>
    </div>

    <div id="total_box">
      <ul id="href_container">
        <li 
          v-for="(item, index) in specialities" 
          :key="item.Название"
          class="href_box">
          <a
            class="href_specialities"
            href="#desc_specialities"
            @click="activeItem = index"> {{ item.Название }} </a>
        </li>
      </ul>
      <div id="text_box">
        <p>{{ specialities[activeItem].Описание }}</p>
        <a :href="'specialities/' + specialities[activeItem].id"><u><i>Подробнее</i></u></a>
      </div>

    </div>
    <div id="column_text">
      <p>Разнообразный и богатый опыт говорит нам, что высококачественный 
      прототип будущего проекта способствует повышению качества 
      благоприятных перспектив! Господа, современная методология 
      разработки влечет за собой процесс внедрения и модернизации благоприятных перспектив. 
      В целом, конечно, постоянное информационно-пропагандистское обеспечение 
      нашей деятельности предопределяет высокую востребованность экономической 
      целесообразности принимаемых решений. </p>
    </div>
    <footer>
      <Downfooter />
    </footer>
  </div>
</template>

<script>
import Topmenu from '~/components/Topmenu.vue'
import Downfooter  from '~/components/Downfooter.vue'
import Middle  from '~/components/Middle.vue'

import constants from "assets/constants";

export default {
  components: {
    Topmenu,
    Downfooter,
    Middle
  },
  asyncData: async function({$axios}) {
      const response = await $axios.get(constants.baseUrl + '/specialities')
        return {
           specialities: response.data,
           activeItem: 0
      }
  }, 
  head() {
    return{
      title: 'Проект "Путевка в жизнь"',
      meta: [
        {hid: 'description', 'name':'description', 'content': 'Профориентационный проект "Путевка в жизнь" для абитуриентов Нижегородской области и их родителей'}
      ]
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat|Roboto+Slab');
#href_container{
  padding-left: 0px;
  /* z-index: 2; */

  opacity: 1;
  transition: width 0.1s, opacity 0.4s;
  z-index: 999999;

}
.href_specialities {
  display: block;
  width: 366px;
  height: 56px;
  padding: 17px;
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: normal;
  line-height: normal;
  font-size: 18px;
  text-decoration: none;
  color: #41505c;
}
.href_box{
  position: relative;
  list-style-type: none;
  position: relative;
}
.href_specialities:focus {
  background-image: url('/images/middle/rectangle.png');
  background-size: cover;
  font-weight: bold;
  color: #ffffff;
}
#text_box{
  position: relative;
  left: -1.4%;
  z-index: 1;
  background: #FFFFFF;
  box-shadow: 0px 2px 11px rgba(85, 102, 129, 0.15);
  width: 816px;
  padding-right: 64px;
  padding-left: 73px;
  padding-top: 33px;
  

  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: normal;
  line-height: 29px;
  font-size: 15px;
  color: #1D262D;
}
#spec_group{
  margin-bottom: 40px;
  margin-left: 117px;
  display: flex;
}
.spec_group_text{
  font-family: 'Roboto Slab', serif;
  font-style: normal;
  font-weight: bold;
  line-height: normal;
  font-size: 20px;
  text-align: center;
  text-transform: uppercase;
  color: #FE5E5D;

  padding-bottom: 6px;
  padding-right: 19px;
  padding-left: 19px;

  border-bottom: 4px solid #FE5E5D;
}
#total_box{
  display: flex;
  margin-left: 117px;
  margin-right: 157px; 
}
#column_text{
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: normal;
  line-height: 29px;
  font-size: 15px;

  color: #1D262D;

  column-count: 2;
  column-gap: 35px;
  margin-left: 124px;
  margin-top: 93px;
  margin-right: 117px;

}
</style>
