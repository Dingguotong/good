<template>
  <div id="app">
    
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="scss" scoped>

#app {
  div,ul,li,ol,p,span,img,h4,h3{
  margin: 0;
  padding: 0;
  list-style: none;
  }
}

</style>
