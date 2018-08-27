# Hash Router for Vue.js
## Usage
Simple to use -- just include it in one of your Vue components that you want hash routing to be activated on.

Example:
``` html
<template>
  <div id="app">
    <!-- include the Router component and pass it the routes object -->
    <Router v-bind:routes="routes" /> 
  </div>
</template>

<script>
  import Vue from 'vue';
  import Router from './hash-router.vue'

  import Home from './home.vue'
  import MyComponent from './my-component.vue'
  import NotFound from './notfound.vue'

  // routes to pass to the router
  // make sure to import required components above
  const routes = {
      '/#': Home,
      '/': Home,
      '/#my-component': MyComponent,
      'NotFound': NotFound,
    };
  
  export default {
    data: function() {
      return {
        routes
      }
    },
    components: {
      Router
    }
  }
</script>
```