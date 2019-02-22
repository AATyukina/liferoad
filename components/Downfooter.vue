<template>
  <div class="total_footer_container">
    <span id="project_name">Проект «Путевка в жизнь», {{ cur_year }} &copy;</span>
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
export default {
  data: function(){
     return{
       cur_year:0
     }
   },
  mounted: function() {
    var now = new Date();
    this.cur_year = now.getFullYear()
   }
}
</script>


<style>
  .total_footer_container{
    border-top: 1px solid #C0C3C6;
    display: flex;
    justify-content: space-between;
    align-items:center;
    padding-left: 117px;
    padding-right: 117px;
    padding-bottom: 41px;
    padding-top: 43px;
    margin-top: 85px;
  }
  #project_name{
    font-family: Montserrat;
    font-style: normal;
    font-weight: 500;
    line-height: normal;
    font-size: 15px;
    color: #2C373F;
  }
  .img_container{
  display: inline-flex;
  justify-content: space-between;
  align-items: center;
}
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
</style>

