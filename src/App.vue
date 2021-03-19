<template>
  <div id="app">
    <FilterNav  :productType='productType' :searchData='searchData' @productTypeWasUpdated="productTypeUpdate" @productSearchWasUpdated="productSearchUpdate"  />
    <Content :productType='productType' :searchData='searchData'  :data='data'  />
    <Pagination/>

  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import FilterNav from './components/FilterNav'
// import database from '../public/database/products.json'
import Content from './components/Content'
import Pagination from './components/Pagination'
import axios from "axios"
export default {
  name: 'App',
  data(){
    return{
      data: null,
      productType: "default",
      searchData:"",
      dataTotal:null,
    }
  },
  components: {
    FilterNav,
    Content,
    Pagination,
  },
  methods:{
    productTypeUpdate:function(value){
      if(value=="default"){
        this.data=this.dataTotal;
        return;
      }
      this.productType=value;
      console.log(this.productType);
      this.data=this.dataTotal.filter((item)=>{return item.type==value;})
      console.log(this.data);
    },
    productSearchUpdate:function(value){
      this.searchData=value; 
      this.data=this.dataTotal.filter((item)=>{
        return item.title.toLowerCase().includes(this.searchData);
      })
    }
  },
  beforeCreate(){
    axios.get("./database/products.json")
    .then(response=>{
      this.dataTotal=response.data.products;
      this.data=this.dataTotal;
      console.log(response.data.products);
    })
    .catch(err=>{
      console.log(err);
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
