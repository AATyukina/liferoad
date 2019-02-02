<template>
  <div>
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
      <div
        v-for="page in pages"
        :key="page"
        class="child">
        <a>{{ page.Название }}</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
   asyncData: async function({$axios}) {
    const response = await $axios.get('http://185.158.153.91:1380/pages')
    return{
      pages: response.data
    }
   }
}
</script>

<style>
 #lr{
   background-color: lightgray;
   padding: 10px;
   display: inline-flex;
   justify-content: flex-end;
   width: 100%;  
   justify-content: space-between;
   align-items: center;
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
  background-color: darkseagreen;
}
.unspechref{
  font-family: 'Times New Roman', Times, serif; 
  font-size: 200%; 
  color: white;
}
</style>




