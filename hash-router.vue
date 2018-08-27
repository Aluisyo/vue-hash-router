<script>
  import Vue from 'vue';

  const Router = Vue.component('Router', {
    data() {
      let path = window.location.pathname;
      const last = path.length - 1;
      path = path !== '/' && path[last] === '/' ? path.slice(0,last) : path

      return {
        currentRoute: path + window.location.hash
      }
    },
    props: {
      routes: Object
    },
    created: function() {
      window.addEventListener('popstate', () => { 
        let path = window.location.pathname;
        const last = path.length - 1;
        path = path !== '/' && path[last] === '/' ? path.slice(0,last) : path
        // debugger;
        this.currentRoute =  path + window.location.hash
      })
    },
    computed: {
      viewComponent() {
        return this.routes[this.currentRoute] || this.routes['NotFound'];
      }
    },
    render(createElement) {
      return createElement(this.viewComponent)
    },
  });

  export default Router;
</script>