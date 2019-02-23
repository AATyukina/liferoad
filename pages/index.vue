<template>
  <div class="wrapper">
    <topmenu />
    <middle />
    <div id="spec_group">
      <div class="spec_group_text">IT</div>
    </div>
    <div id="total_box">
      <div id="sp_box">
        <div 
          v-for="(item, index) in specialities"
          :key="item">
          <div 
            v-if="activeItem == index"
            class="href_filled_box">
            <a 
              href="#text_box"
              @click="activeItem = index">{{ item.Название }}</a>
          </div>
          <div 
            v-else
            class="href_empty_box">
            <a 
              href="#text_box"
              @click="activeItem = index">{{ item.Название }}</a>
          </div>
        </div> 
      </div>
      <div id="text_box">
        <p>{{ specialities[activeItem].Описание }}</p>
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
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat|Roboto+Slab');
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
  justify-content: space-between;
}
#text_box{
  background: #FFFFFF;
  box-shadow: 0px 2px 11px rgba(85, 102, 129, 0.15);
  width: 69%;/* width: 816px; */
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
/* #sp_box{
  width: 366px;
} */
.href_filled_box{
  background-image:url("/images/middle/rectangle2.png");
  padding-left: 18.7px;
  padding-top: 17px;
  padding-bottom: 17px;
  height: 56px;
  width:366px ;
}
.href_empty_box{
  padding-left: 18.7px;
  padding-top: 17px;
  padding-bottom: 17px;
  height: 56px;
  width: 366px;
}
div.href_filled_box a{
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: bold;
  line-height: normal;
  font-size: 18px;

  color: #FFFFFF;
}
div.href_empty_box a{
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: normal;
  line-height: normal;
  font-size: 18px;

  color: #1D262D;
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
