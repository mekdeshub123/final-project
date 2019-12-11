<template>
  <div id="app">
    
    <nav>
      <img src="./assets/track-logo.png">
      
      <router-link to="/">Update</router-link>
      <router-link to="/RecordTable">Record</router-link>
    </nav>
    <router-view />
  <!-- <RecordForm></RecordForm>
  <RecordTable></RecordTable> -->

  </div>
</template>

<script>
//import RecordForm from './components/RecordForm'
//import RecordTable from './components/RecordTable'

export default {
  name: 'app',
  components: {
  }
}
</script>

<style>
nav {
  padding: 20px 20px 20px 0;
}
nav a {
  padding: 10px;
  font-size: 28px;
  text-decoration:none;
  background: #fff;
  border-radius: 5px;
  color: rgb(0, 110, 255);
  font-weight: bold;
  margin-right: 15px;
}
</style>