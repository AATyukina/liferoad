<template>
  <div class="total_container">
    <div class="href_container">
      <a
        class="href_a"
        href="../news/1">Новости</a> 
      <a 
        v-for="item in items"
        :key="item"
        :href="'../' + item.slug"
        class="href_a">{{ item.Название }}</a>
    </div>
    <div class="img_container">
      <a>
        <img 
          id="img_twitter"
          src="~/static/images/header_footer/twitter.png">
      </a>
      <a>
        <img 
          id="img_facebook"
          src="~/static/images/header_footer/facebook.png">
      </a>
      <a>
        <img 
          id="img_mail"
          src="~/static/images/header_footer/mail.png">
      </a>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import constants from "assets/constants";

export default {
   data: function(){
     return{
       items: []
     }
   },
   mounted: async function() {
    const response = await axios.get(constants.baseUrl + '/pages')
    this.items = response.data
   }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat|Roboto+Slab');

#img_twitter{
  width: 24px;
  height: 19.64px;
  margin-right: 52px;
}
#img_facebook{
  width: 24px;
  height: 24px;
  margin-right: 52px;
}
#img_mail{
  width: 26px;
  height: 17.23px;
  margin-right: 52px;
}
.href_a{
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 500;
  line-height: normal;
  font-size: 15px;
  color: #2C373F;
  margin-right: 52px;
  text-decoration: none;
}
.total_container{
  margin-top: 49px;
  padding-right: 117px; 
  padding-left: 117px;
  margin-bottom: 47px; 
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.img_container{
  display: inline-flex;
  justify-content: space-between;
  align-items: center;
}
.href_container{
  display: inline-flex;
  justify-content: space-between;
}
</style>