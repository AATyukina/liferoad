<template>
  <div id="total_container">
    <div id ="lr">
      <a 
        id="lrhref" 
        href="../">Путевка в жизнь</a>
      <a 
        class="unspechref"
        href="../universities/">ВУЗы</a>
      <a
        class="unspechref"
        href="../specialities/">Специальности</a>
    </div>
    <div class="parent">
      <a
        href="../news/1" 
        class="child">Новости</a>
      <div
        v-for="item in items"
        :key="item"
        class="child">
        <a :href="'../' + item.slug">{{ item.Название }}</a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
   data: function(){
     return{
       items: []
     }
   },
   mounted: async function() {
    const response = await axios.get('http://185.158.153.91:1380/pages')
    this.items = response.data
   }
}
</script>

<style>
 #total_container{
 background-color: lightpink;
}
 #lr{
   padding: 10px;
   display: inline-flex;
   justify-content: flex-end;
   width: 100%;  
   justify-content: space-between;
   align-items: baseline;
 }
 #lrhref{
   font-family: 'Times New Roman', Times, serif; 
   font-size: 300%; 
   flex-grow: 0.5;
   color: black;
 }
 #otherhref{
  display: inline-flex;
  justify-content: flex-end;
  width:75%;
 }
 .parent{
	display: inline-flex;
  justify-content: flex-end;
  width: 100%;  
}
.child{
  font-family: 'Times New Roman', Times, serif; 
  font-size: 130%; 
  margin-right: 10px;
  margin-left: 10px;
  color: white;
}
.unspechref{
  font-family: 'Times New Roman', Times, serif; 
  font-size: 200%; 
  color: white;
}
</style>