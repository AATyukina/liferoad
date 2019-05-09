<template>
  <div class="total">
    <topmenu />
    <div id="univer_cont">

      <div id="project_desc">
        <h1 class="title">
          Путевка в жизнь
        </h1>
        <div class="column_text">
          <p>Разнообразный и богатый опыт говорит нам, что высококачественный 
          прототип будущего проекта способствует повышению качества 
          благоприятных перспектив! Господа, современная методология 
          разработки влечет за собой процесс внедрения и модернизации благоприятных перспектив. 
          В целом, конечно, постоянное информационно-пропагандистское обеспечение 
          нашей деятельности предопределяет высокую востребованность экономической 
          целесообразности принимаемых решений. </p>
        </div>
      </div>

      <div id="brief_info_university"> 
        <div class="img_container">
          <img 
            class="logo_img"
            src="~/static/images/universities/university_logo.png">
        </div>
        <div class="text_container">
          <div class="header_container">
            <h1 class="un_header">{{ university.Название }}</h1>
          </div>
          <div class="info_container">
            {{ university.Описание }}
          </div>
        </div>
      </div>

      <div id="video_container"/>

      <div class="column_text">
        <p>Разнообразный и богатый опыт говорит нам, что высококачественный 
        прототип будущего проекта способствует повышению качества 
        благоприятных перспектив! Господа, современная методология 
        разработки влечет за собой процесс внедрения и модернизации благоприятных перспектив. 
        В целом, конечно, постоянное информационно-пропагандистское обеспечение 
        нашей деятельности предопределяет высокую востребованность экономической 
        целесообразности принимаемых решений. </p>
      </div>

      <div id="prof_container"> 
        <h1 class="un_header">Профессии</h1>
        <div id="prof_list">
          <div 
            v-for="speciality in university.специальность"
            :key="speciality"
            class="prof_list_unit">
            <a 
              :href="'/specialities/' + speciality.id"
              class="prf_href"> {{ speciality.Название }} </a>
            <div class="faculties">
              <p>Программная инженерия</p>
              <p>Бизнес - информатика</p>
            </div>
            <div class="exams">
              <p>Математика</p>
              <p>Физика</p>
              <p>Информатика</p>
            </div>
            <div class="scores">90-100</div>
          </div>
        </div>
      </div>

      <div id="cont_info__container"> 
        <div class="map_container" />
        <div class="contacts_container">
          <h1 class="un_header">Контакты</h1>
          <div class="inner_contacts_container">
            <div id="top_contacts"> 
              <div class="com">
                <img 
                  id="img_path"
                  src="~/static/images/universities/path.png">
                <p>Большая Печёрская ул., 25</p>
              </div>
              <div class="com">
                <img
                  id="img_call"
                  src="~/static/images/universities/call.png">
                <p>{{ university.Телефон }}</p>
              </div>
              <div class="com">
                <img
                  id="img_mail"
                  src="~/static/images/universities/mail.png">
                <p>{{ university.Email }}</p>
              </div>
            </div>

            <div id="down_contacts">
              <div class="com">
                <img
                  id="img_vk"
                  src="~/static/images/universities/vk.png">
                <p>vk</p>
              </div>
              <div class="com">
                <img
                  id="img_face"
                  src="~/static/images/universities/facebook.png">
                <p>facebook</p>
              </div>
            </div>

          </div>
        </div>
      </div>
    </div>
    <footer>
      <Downfooter />
    </footer>
  </div>
</template>

<script>
import Topmenu from '~/components/Topmenu.vue'
import Downfooter  from '~/components/Downfooter.vue'
import constants from "assets/constants";
export default {
  components: {
    Topmenu,
    Downfooter
  },

  asyncData: async function({$axios, params}) {
    const response = await $axios.get(constants.baseUrl + '/universities?%D0%9A%D0%BE%D0%B4='+ params.id)
    return {
       university: response.data[0]
    }
  },
     head() {
    return{
      title: this.university.Название + '. Проект "Путевка в жизнь"',
      meta: [
        {hid: 'description', 'name':'description', 'content': 'Профориентационный проект "Путевка в жизнь" для абитуриентов Нижегородской области и их родителей. Университет' + this.university.Название}
      ]
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat|Roboto+Slab');
.total{
  width: 2000px;
  margin: 0 auto;
}
#univer_cont{
  margin-left: 157px;
  margin-top: 46px;
  margin-right: 157px;
  margin-bottom: 80px;
}
#project_desc{
  margin-bottom: 56px;
}
#project_desc .title{
  width: 238px;
  height: 32px;

  font-family: 'Roboto Slab', serif;
  font-style: normal;
  font-weight: bold;
  font-size: 24px;
  line-height: 32px;
  text-transform: uppercase;

  color: #5D3DC6;

  margin-bottom: 26px;
}
.column_text{
  column-count: 2;
  column-gap: 40px;

  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 15px;
  line-height: 29px;

  color: #1D262D;
  margin-bottom: 56px;
}
#brief_info_university{
  margin-bottom: 52px;
  display: flex;
}
#brief_info_university #img_container{
  margin-right: 77px;
  
}
.logo_img{
  margin-right: 77px;
  width: 190px;
  height: 184px;
}
#brief_info_university .header_container{
  margin-bottom: 26px;
}
.info_container{
  /* width: 859px;
  height: 147px; */

  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 15px;
  line-height: 29px;

  color: #1D262D;
}
.un_header{
  width: 380px;
  height: 32px;

  font-family: 'Roboto Slab', serif;
  font-style: normal;
  font-weight: bold;
  font-size: 24px;
  line-height: 32px;
  text-transform: uppercase;

  color: #1D262D;
}
#video_container{
  width: 1126px;
  height: 448px;

  box-shadow: 0px 3px 15px #000000;
  border-radius: 10px;

  margin-bottom: 57px;
}
#prof_list{
  width: 1126px;
  margin-top: 25px;

  background: #FFFFFF;
  box-shadow: 0px 2px 11px rgba(85, 102, 129, 0.15);
}
#prof_container{
  margin-bottom: 57px;
}
#cont_info__container{
  display: flex;
  justify-content: space-between;
}
.map_container{
  width: 776px;
  height: 416px;

  box-shadow: 0px 3px 15px #000000;
  border-radius: 10px;
  margin-right: 40px;
}
.inner_contacts_container{
  margin-top: 40px;
}
#top_contacts{
  margin-bottom: 47px;
}
.com{
  margin-bottom: 13px;
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
}
.com img{
  /* width: 14px;
  height: 20px; */

  background: #FFFFFF;
  margin-right: 23px;
}
.com p{
  height: 19px;

  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 15px;
  line-height: 18px;

  color: #1D262D;
}
#img_path{
  width: 14px;
  height: 20px;
}
#img_mail{
  width: 20px;
  height: 12px;
  margin-right: 23px;
}
#img_call{
    width: 16px;
  height: 16px;

}
#img_vk{
  width: 21px;
  height: 13px;
}
#img_face{
  width: 11px;
  height: 22px;
  margin-right: 23px;
}
.prof_list_unit{
  display: flex;
  justify-content: space-between;
  align-items: flex-start;

  /* padding: 25px, 20px, 25px, 20px; */
  padding-top: 25px;
  margin-right: 20px;
  padding-bottom: 25px;
  margin-left: 20px;

  border-bottom: 1px solid #C0C3C6;
}
.prf_href{
  width: 230px;
  height: 22px;

  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 600;
  font-size: 18px;
  line-height: 22px;

  color: #1D262D;
}
.faculties{
  width: 220px;

  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 15px;
  line-height: 18px;/* identical to box height */

  color: #1D262D;

}
.exams{
  width: 95px;

  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 15px;
  line-height: 18px;/* identical to box height */

  color: #1D262D;
}
.scores{
  width: 83px;
  height: 30px;

  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: bold;
  font-size: 24px;
  line-height: 29px;/* identical to box height */
  text-align: right;

  color: #1D262D;
}
</style>