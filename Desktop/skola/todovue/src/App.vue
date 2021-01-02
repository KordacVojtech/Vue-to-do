<template>
  <div>
    <HeaderTop />
    <div class="tableDiv">
      <Table />
    </div>
  </div>
</template>

<script>

import HeaderTop from './components/HeaderTop'
import Table from './components/Table'

export default {
  name: 'App',
  components:{
    HeaderTop,
    Table
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

.tableDiv{
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 80vh;
}

body{
  background-color: rgb(190, 190, 190);
  animation: pulse 2s ease-in;
}

@keyframes pulse{
    0% {
    background-color: #4cfd06;
  }
  100% {
    background-color: rgb(190, 190, 190);
  }
}
</style>
