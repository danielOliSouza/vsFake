<template>
  <div id="app">
    <!-- div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/ -->
    <div id="container">
      <b-row id="line">
        <b-col id="menu-left" cols="3" sm="3" md="3" lg="3" xl="3">
          Menu Lateral
        </b-col>
        <b-col id="body-work" cols="9" sm="9" md="9" lg="9" xl="9">
          <div id="code">
            <code-work></code-work>
          </div>
          <div id="terminal">
            Terminal
          </div>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
import CodeWork from '@/components/CodeWork'

export default {
  name: "app",
  components: {
    CodeWork
  },
  created(){

  }
}
</script>


<style lang="scss" scoped>
  #app{
    background-color: #1e1e1e;
    width: 99%;
    height: 100%;
    position: absolute;
    padding: 0;
  }
  #container{
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
    position: relative;
    z-index: 500;
    font-size: 14px;
    font-family: Monaco, Menlo, Consolas, "Droid Sans Mono", "Inconsolata", "Courier New", monospace; 
  }
  #line{
    position: relative; 
    height: 100%;
  }
  #menu-left{
    background: #252526;
    position: relative;
    height: 100%;
    color: #FFF;
  }
  #body-work{
    margin: 0;
    padding: 0;
  }
  #code{
    height: 65%;
    border-bottom: 0.8px solid #AAA ;
    color: #2568ca;
  }
  #terminal{
    color: #FFF;
  }
</style>
