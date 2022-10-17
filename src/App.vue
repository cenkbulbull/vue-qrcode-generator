<template>
  <div id="app">
   <div class="container">
     <div class="form-group w-50 mt-5 mx-auto d-flex flex-column align-items-center urlDiv">
       <input v-on:keydown.enter="value=url" v-model="url" class="form-control" placeholder="Url Girin (örn:www.cenkbulbul.com ya da cenkbulbul.com)" />
       <button @click="value=url" class="btn btn-outline-success my-3">Oluştur</button>
     </div>
     <div class="card w-25 mx-auto mt-5">
      <div class="text-center qr d-flex align-items-center justify-content-center">
        <qrcode-vue :value="'http://'+ value" :size="size" level="H" render-as="svg" background="transparent" foreground="#ffffff"/>
      </div>
      <div v-if="value!=''" class="card-body text-center">
        <p>{{value}}</p>
        <a :href="'http://'+ value" target="blank" class="btn btn-primary">Siteye Git</a>
      </div>
    </div>
  </div>
  
</div>
</template>

<script>
  import QrcodeVue from 'qrcode.vue'

  export default {
    data () {
      return {
        url:"",
        value:"",
        size: 120,
      }
    },
    components: {
      QrcodeVue,
    }
  }
</script>

<style>
  body{
    background-color: #d6e1f0;
  }
  .card{
    width: 220px !important;
    border-radius: 10px;
    font-size: 11px;
  }
  .btn{
    font-size: 13px;
  }
  .qr{
    height: 200px !important;
    background-color:#2b7efa ;
    border-radius: 10px;
    padding: 20px;
    margin: 10px;
  }

  @media only screen and (max-width: 576px) {
    .urlDiv{
      width: 100% !important;
    }

  }


</style>
