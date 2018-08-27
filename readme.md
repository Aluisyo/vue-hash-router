# Hash Router for Vue.js
## Features
1. Simple hash-based routing - note that you should manually include the # in your routes.
1. Supports params in the routes, will pass props through to the component using the name provided in the route. eg: `product/:id` will pass an `id` prop to the component specified in the route.
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
  import Product from './product.vue'

  // routes to pass to the router
  // make sure to import required components above
  const routes = {
      '/#': Home,
      '/': Home,
      '/products/:id': Product
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

You can also extract the routes into a separate file, like so:

*routes.js*:
``` js
import Home from './home.vue'
import MyComponent from './my-component.vue'
import NotFound from './notfound.vue'
import Product from './product.vue'

// routes to pass to the router
// make sure to import required components above
const routes = {
  '/#': Home,
  '/': Home,
  '/products/:id': Product
  '/#my-component': MyComponent,
  'NotFound': NotFound,
};
```

*app.vue*:
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
  import routes from './routes'
  
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
