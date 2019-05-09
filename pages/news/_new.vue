<template>
  <div class="total">
    <topmenu />
    <div id="news_container">
      <h3 class="news_title"> Новости </h3>
      <div v-if="flag">
        <div class="news_list">
          <div 
            v-for="n in news"
            :key="n"
            class="news_list_unit">
            <a :href="'details/' + n.id">{{ n.Название }}</a>
            <p>{{ n.Кратко }}</p>
          </div>
        </div>
        <div class="bot_container">
          <div
            v-for="number in buttom_amount"
            :key="number"
            class="btm">
            <a :href="'/news/' + number"><b>{{ number }}</b></a>
          </div>
          <!-- <div
            v-if="number==counter" 
            class="btm">
            <a :href="'/news/' + number"><b>{{ number }}</b></a>
          </div> -->
          <!-- <div 
            v-else
            class="btm">
            <a :href="'/news/' + number">{{ number }}</a>
          </div> -->
        </div>
      </div>
      <div v-else> 
        <h2>Oops! Page not found! But don't worry! <br> Error code  {{ code }}</h2>
      </div>
    </div>
  </div>
</template>

<script>
import Topmenu from '~/components/Topmenu.vue'
import constants from "assets/constants";

let pageAmount = 2
export default {
    components: {
    Topmenu
  },
  asyncData: async function({$axios, params}) {
    try{
    const response = await $axios.get(constants.baseUrl + `/news?_limit=${pageAmount}&_start=${(params.new - 1)*pageAmount}`)
    const ba = await $axios.get(constants.baseUrl + `/news/count`)
    var buttom_amount = Math.floor( ba.data / pageAmount ) + (ba.data%pageAmount>0?1:0)
    return {
       buttom_amount,
       news: response.data,
       counter: params.new,
       flag: true
    }
  }catch(error){
    return{
          flag: false, 
          code: error.response.status
        }
  } 
  },
     head() {
    return{
      title: 'Новости. Проект "Путевка в жизнь"',
      meta: [
        {hid: 'description', 'name':'description', 'content': 'Новости. Профориентационный проект "Путевка в жизнь" для абитуриентов Нижегородской области и их родителей.'}
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
  .bot_container{
    display: flex;
    margin-top: 50px;
    justify-content: center;
  }
  .btm{
    border-bottom: 1px solid #C0C3C6;
    text-align: center;
    margin: 5px;
    width: 10px;
  }
  .btm a{
    font-family: 'Roboto Slab', serif;
    font-style: normal;
    font-weight: bold;
    color: #5D3DC6;
    font-size: 20px;
    line-height: 20px;
  }
  #news_container{
    margin-left: 117px;
    margin-top: 46px;
    margin-right: 117px;
    margin-bottom: 80px;
  }
  .news_title{
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
  .news_list{
    width: auto;
    margin-top: 25px;

    background: #FFFFFF;
    box-shadow: 0px 2px 11px rgba(85, 102, 129, 0.15);
  }
  .news_list_unit{
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

</style>

