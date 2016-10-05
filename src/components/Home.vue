<template>
  <div>
    <!--<header-component/>-->
    <div><h1>{{ msg }}</h1></div>
    <!--<other-component/>-->
  </div>
</template>

<script>
  //    import HeaderComponent from './components/header.vue'
  //    import OtherComponent from './components/other.vue'
  export default{
    data () {
      return {
        msg: 'hello vue'
      }
    }
//    components: {
//      'other-component': OtherComponent,
//      HeaderComponent,
//    }
  }
</script>
