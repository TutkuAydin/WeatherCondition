
<template>
 <div class="App">
   
    <Bar/>
    
    <Home/>
   
  </div>
</template>

<script>
import Bar from '@/components/Bar'
import Home from  '@/views/Home'
export default {
  name: 'App',
  components: {
    Bar,
    Home,
  },

  data(){

    //
  }
};
</script>
