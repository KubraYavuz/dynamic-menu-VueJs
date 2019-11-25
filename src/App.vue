<template>
  <div>
    <nav class="navbar navbar-inverse">
      <div class="container-fluid">
        <div class="navbar-header">
          <a class="navbar-brand" href="#appHome">WebSite</a>
        </div>
        <ul class="nav navbar-nav">
          <li><a href="#appHome" @click="selectedComponent = 'appHome'">Home</a></li>
          <li><a href="#appAbout" @click="selectedComponent = 'appAbout'">About</a></li>
          <li><a href="#appContact" @click="selectedComponent = 'appContact'">Contact</a></li>
        </ul>
      </div>
    </nav>
    <component :is="selectedComponent"></component>
  </div>
</template>

<script>
  import Home from "./components/Home";
  import About from "./components/About";
  import Contact from "./components/Contact";
  export default {
    data:function(){
      return{
        selectedComponent : ""
      }
    },
    components:{
      appHome : Home,
      appAbout : About,
      appContact : Contact
    }
  }
</script>
<style></style>