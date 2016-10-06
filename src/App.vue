<template>
  <div id="app">
    <div class="form">

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
          <input type="text" class="form-control" v-model="VPM.token_name" placeholder="Token Name">
          <span class="input-group-addon" @click="getTokenFromLocalStorage">Get it!</span>
        </div>
        <textarea class="form-control">{{ VPM.token }}</textarea>
      </div>


      <div class="form-group">
        <label>Data</label>
        <textarea class="form-control" v-model="VPM.data"></textarea>
      </div>

      <div class="form-group">
        <button v-for="item in methods" class="btn" v-bind:class="[item.class]" @click="send(item.name)">{{item.name}}
        </button>

        <!--<button class="btn btn-default" @click="send(1)">GET</button>
        <button class="btn btn-primary"  @click="send(2)">POST</button>
        <button class="btn btn-success" @click="send(3)">PUT</button>
        <button class="btn btn-info" @click="send(4)">PATCH</button>
        <button class="btn btn-danger" @click="send(5)">DELETE</button>-->
      </div>

      <div class="form-group">
        <label>Status code:{<span class="">{{ VPM.status }}</span>} text:{<span>{{ VPM.status_text }}</span>}</label>
      </div>

      <div class="form-group">
        <label>Content</label>
        <textarea class="form-control" rows="5">{{ VPM.content }}</textarea>
      </div>
    </div>
  </div>
</template>

<script>
  // import Hello from './components/Hello'
  // import Home from './components/Home'

  export default {
    data () {
      let token = window.localStorage.token
      return {
        VPM: {
          headers: {
            'content-type': 'application/json',
            'cache-control': 'no-cache'
          },
          data: '',
          content: 'test',
          status: '000',
          status_text: 'prepared',
          token_name: 'token',
          token: token
        },
        methods: [{
          'name': 'GET',
          'class': 'btn-default'
        }, {
          'name': 'POST',
          'class': 'btn-primary'
        }, {
          'name': 'PUT',
          'class': 'btn-success'
        }, {
          'name': 'PATCH',
          'class': 'btn-info'
        }, {
          'name': 'DELETE',
          'class': 'btn-danger'
        }]
      }
    },
    methods: {
      getTokenFromLocalStorage: function () {
        var tokenName = this.VPM.token_name
//        this.$set('VPM.token', window.localStorage[tokenName])
        this.VPM.token = window.localStorage[tokenName]
        console.log(this.VPM.token)
      },
      sentRequest: function (method) {
        let vpm = this.VPM
        console.log(vpm.data)
        this.$http({
          method: method,
          url: vpm.url,
          data: vpm.data,
          headers: vpm.headers,
          emulateJSON: true
        }).then((response) => {
          vpm.status = response.status
          vpm.status_text = response.statusText
          vpm.content = response.body
          console.log(response)
        }, (response) => {
          console.log(response)
          vpm.status = response.status
          vpm.status_text = response.statusText
          vpm.content = response.body
        })
      },
      send: function (method) {
        this.sentRequest(method)
        console.log(method)
      }
    }
  }
</script>

<style>
  /*html {
  height: 100%;
  }

  body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  }

  #app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
  }

  #app a {
  color: #42b983;
  text-decoration: none;
  }

  .logo {
  width: 100px;
  height: 100px
  }*/
</style>
