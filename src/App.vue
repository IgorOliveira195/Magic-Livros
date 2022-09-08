<template>
  <Navbar/>
  <router-view/>
  <Footer/>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'

export default{
  name: 'Home',
  components:{
    Navbar,
    Footer
  }
}

</script>

<style>
  *{
  padding:0;
  margin:0;
  vertical-align:baseline;
  list-style:none;
  border:0
  }

  body{
     background-color: #B2E0F5;
  }

</style>
