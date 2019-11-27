<template>
  <div class="page">
    <div id="app">
      <div class="translate-wrap">
      <img id="trans" class="hide" src="./assets/sxc.gif" style="width:100px; heigth:200px" />
        <TOW @sendContent="send"></TOW>
        <div class="translateio">
          <InContext @getContent="fyContent" class="left" />
          <OutContext :showContent="show" class="right" />
        </div>
      </div>
      <Btm class='btm' />
    </div>
  </div>
</template>

<script>
import InContext from './components/InContext'
import OutContext from './components/OutContext'
import TOW from './components/transOperationWrapper'
import Btm from './components/bottom'
import axios from 'axios'
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
    TOW,
    Btm
  },
  methods: {
    fyContent (content) {
      this.content = content
    },
    send (isSend) {
      document.getElementById('trans').classList.remove('hide')
      this.isSend = isSend
      let _this = this
      axios.post('http://47.98.138.95:80/test/leeyw/api/v1.0/cxhFanyi/fenci', {
        str: this.content
      })
        .then(function (response) {
          console.log(response.data.cxhList)
          _this.show = ''
          for (let i = 1; i < response.data.cxhList.length; i++) {
            let ii = Math.random() * 10 > 5 ? 0 : 1
            let showContent = []
            if (typeof (response.data.cxhList[i].emoji_tag) === 'string') {
              showContent[i] = response.data.cxhList[i].emoji_tag
              _this.show += showContent[i]
            } else {
              if (response.data.cxhList[i].emoji_tag[ii]) {
                showContent[i] = response.data.cxhList[i].emoji_tag[ii]
                _this.show += showContent[i]
              } else {
                showContent[i] = response.data.cxhList[i].emoji_tag[0]
                _this.show += showContent[i]
              }
            }
          }
          document.getElementById('trans').classList.add('hide')
          console.log(_this.show)
        })
        .catch(function (error) {
          console.log(error)
        })
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
.page{
  height:100%;width:100%;
  /*width: 100%;*/
  position:fixed;
  background-size: cover;
  background-attachment: fixed;
  background:url(assets/bg.png) no-repeat center center;
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
  position: relative;
}
.translate-wrap{
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
#trans{
  position: absolute;
  top:50%; left:50%;
  margin-top: -80px;
  margin-left: -50px;
  border: 15px solid black;
  border-radius: 20px;
  z-index: 10;
}
.hide{
  visibility:hidden;
}
.btm{
  position: absolute;
  bottom:-200%;
}
</style>
