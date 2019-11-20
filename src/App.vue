<template>
  <div id="app">
    <div class="translate-wrap">
      <TOW @sendContent="send"></TOW>
      <div class="translateio">
        <InContext @getContent="fyContent" class="left" />
        <OutContext :showContent="show" class="right" />
      </div>
    </div>
  </div>
</template>

<script>
import InContext from './components/InContext'
import OutContext from './components/OutContext'
import TOW from './components/transOperationWrapper'
export default {
  name: 'App',
  data () {
    return {
      content: '',
      isSend: false,
      show: ''
    }
  },
  components: {
    InContext,
    OutContext,
    TOW
  },
  methods: {
    fyContent (content) {
      this.content = content
    },
    send (isSend) {
      this.isSend = isSend
      let tmp = this.content
      this.show = tmp
      console.log(this.show)
      this.isSend = false
    }
  }
}
</script>

<style>
*{
            margin: 0;
        padding: 0;
      }
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
}
.translate-wrap{
    border: 2px solid red;
    heigth: 360px;
    width: 929px;
}
.translateio {
  display: flex;
  justify-content: center;
  heigth: 139px;
  width: 100%;
}

.left .right{
  flex: 1;
}
</style>
