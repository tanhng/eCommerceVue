<template>
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item button " >
        <button class="nav-link " v-on:click="updateType('default')"  href="#">All</button>
      </li>
      <li class="nav-item button" >
        <button class="nav-link " v-on:click="updateType('phone')"  href="#">Phone</button>
      </li>
      <li class="nav-item button">
        <button class="nav-link"  v-on:click="updateType('laptop')"  href="#">Laptop</button>
      </li>
    </ul>
  </div>
</nav>
</template>

<script>

export default {
  name: 'FilterNav',
  props:['productType'],
  components: {

  },
  methods:{
    updateType: function(type){
      this.$emit('productTypeWasUpdated',type);
    }
  }
}
</script>

<style>
.button{
  padding:auto;
  margin:20px;
}
</style>
