<template>
  <div id="app">
    <form role="form">

      <div class="form-group">
        <label>Address</label>
        <input type="text" class="form-control" v-model="VPM.url">
      </div>

      <div class="form-group">
        <label>Headers</label>
        <textarea class="form-control" v-model="VPM.headers"></textarea>
      </div>

      <div class="form-group">
        <div class="input-group">
          <span class="input-group-addon">Token name</span>
          <input type="text" class="form-control" v-model="VPM.token">
        </div>
        <input class="form-control">
      </div>


      <div class="form-group">
        <label>Data</label>
        <textarea class="form-control" v-model="VPM.data"></textarea>
      </div>

      <div class="form-group">
        <button class="btn btn-default" @click="show">GET</button>
        <button class="btn btn-primary">POST</button>
        <button class="btn btn-success">PUT</button>
        <button class="btn btn-info">PATCH</button>
        <button class="btn btn-danger">DELETE</button>
      </div>

      <div class="form-group">
        <label>Status <span class="">{{ VPM.status }}</span></label>
      </div>

      <div class="form-group">
        <label>Content</label>
        <textarea class="form-control" rows="5">{{ VPM.content }}</textarea>
      </div>
    </form>
  </div>
</template>

<script>
  // import Hello from './components/Hello'
  // import Home from './components/Home'

  export default {
    data () {
      return {
        VPM: {
          content: 'test',
          status: '000',
          token: 'token'
        }
      }
    },
    methods: {
      show () {
//        let VPM = this.VPM;

      }
    }
  }
</script>

<style>
  /*html {*/
  /*height: 100%;*/
  /*}*/

  /*body {*/
  /*display: flex;*/
  /*align-items: center;*/
  /*justify-content: center;*/
  /*height: 100%;*/
  /*}*/

  /*#app {*/
  /*color: #2c3e50;*/
  /*margin-top: -100px;*/
  /*max-width: 600px;*/
  /*font-family: Source Sans Pro, Helvetica, sans-serif;*/
  /*text-align: center;*/
  /*}*/

  /*#app a {*/
  /*color: #42b983;*/
  /*text-decoration: none;*/
  /*}*/

  /*.logo {*/
  /*width: 100px;*/
  /*height: 100px*/
  /*}*/
</style>
