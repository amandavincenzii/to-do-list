<template>
  <header>
      <h1>{{titulo}}</h1>
  </header>
</template>

<script>
export default {
  data(){
    return{
      props: ["titulo"], 
    }
  }
}
</script>

<style scoped>
header{
  background-color: royalblue;
  height: 50px;
  width: 100%;
  position: fixed;
  color: white;
  top:0;
  display: flex;
  justify-content: center;
}

h1{
  color: white;
  z-index: 1;
}
</style>