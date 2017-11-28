<template>
  <div>
   <div class="col-md-3" >
     <div class="panel panel-warning" v-for="book in books">
       <div class="panel-heading" >
         {{book.bookName}}
       </div>
       <div class="panel-body text-center" >
         <img :src="book.bookCover" alt="" />
       </div>
       <div class="panel-footer">
         {{book.bookPrice | currency('￥')}}
         <router-link :to = "{name: 'detail', params: {id:book.id}}">查看详情</router-link>
       </div>
     </div>
   </div>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    filters:{
      currency(input,param1){
        return param1 + input
      }
    },
    created(){
      axios.get('/book').then((res)=>{
        this.books = res.data
        console.log(res.data)
      })
    },
    data(){
      return {
        books:[
         
        ]
      }
    },
    component:{

    },
    methods:{}
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img{
  width:150px;
  height: 200px;
}
</style>
