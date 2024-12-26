<template> 
  <div id="app">
    <router-link to="/">Home</router-link> |
    <router-link to="/about/admin">About</router-link>
    <router-view />
    <div class="scrollPosition"> {{ offset }}</div>
    <composition></composition>
   
  </div>
 
</template>

<script>
import mixin from '@/mixin';
import composition from './components/composition.vue';


export default {
name: 'App',
mixins: [mixin],
components: {
  composition,
}
}

</script>


<style>
#app {
width: 100%;
height: 3000px;
position: relative;
}
.scrollPosition {
position: fixed;
left: 10px;
right: 10px;
}
</style>
