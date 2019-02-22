<template>
  <div class="wrapper">
    <topmenu />
    <div class="middle_container">
      <div class="text_container">
        <h1 class="title">
          Путевка в жизнь
        </h1>
        <p id="text"> Разнообразный и богатый опыт говорит нам, 
        что высококачественный прототип будущего проекта способствует 
        повышению качества благоприятных перспектив! 
        Господа, современная методология разработки влечет за собой 
        процесс внедрения и модернизации благоприятных перспектив. 
        В целом, конечно, постоянное информационно-пропагандистское
        обеспечение нашей деятельности предопределяет высокую 
        востребованность экономической целесообразности принимаемых решений.
        </p>
      </div>
      <span>
        <img 
          id="picture"
          src="~/static/images/middle/group_people.png">
      </span>
    </div>
    <footer>
      <Downfooter />
    </footer>
  </div>
</template>

<script>
import Topmenu from '~/components/Topmenu.vue'
import Downfooter  from '~/components/Downfooter.vue'

export default {
  components: {
    Topmenu,
    Downfooter
  }
}
</script>

<style>
.middle_container {
  display: inline-flex;
  justify-content: space-between;
  align-items:center;
}
.text_container{
  margin-left: 117px;
  margin-right: 42px;
}
.title {
  /* position: absolute; */
  width: 476px;
  height: 64px;
  /* left: 117px;
  top: 189px; */
  font-family: Roboto Slab;
  font-style: normal;
  font-weight: bold;
  line-height: normal;
  font-size: 48px;
  text-transform: uppercase;
  color: #5d3dc6;
  margin-bottom: 43px;
}
#picture{
  /* position: absolute; */
  width: 600px;
  height: 496px;
  /* left: 51.02%;
  top: 7.93%; */
}
#text {
  /* position: absolute; */
  width: 582px;
  height: 235px;
  /* left: 117px;
  top: 296px; */
  font-family: Montserrat;
  font-style: normal;
  font-weight: normal;
  line-height: 29px;
  font-size: 15px;
  color: #1d262d;
}
</style>