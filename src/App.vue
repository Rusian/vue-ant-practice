<template>
  <div id="app">
    <DynamicFormItem msg="Welcome to Your Vue.js App"/>
    <OtherFormControls/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import DynamicFormItem from './components/antform/dynamicFormItem.vue'
import OtherFormControls from './components/antform/otherFormControls.vue'

export default {
  name: 'app',
  components: {
    // HelloWorld,
    // 
    OtherFormControls
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
