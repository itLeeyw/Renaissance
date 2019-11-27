<template>
    <div @mousedown="down" @mouseenter="enter"  class="output-warp">
        <div id="context" class="context">{{showContent}}</div>
    </div>
</template>

<script>
export default {
  name: 'OutContext',
  data () {
    return {
    }
  },
  props: ['showContent'],
  methods: {
    down (e) {
      let oInput = document.createElement('input')
      oInput.value = this.showContent
      document.body.appendChild(oInput)
      oInput.select()
      document.execCommand('Copy')
      oInput.style.display = 'none'
      document.body.removeChild(oInput)
      let tips = document.createElement('div')
      tips.value = '复制成功'
      tips.style.left = e.clientX + 5 + 'px'
      tips.style.top = e.clientY + -23 + 'px'
      tips.style.background = '#ccc'
      tips.style.position = 'absolute'
      tips.style.padding = '5px'
      tips.innerHTML = '复制成功'
      document.body.appendChild(tips)
      tips.style.animation = 'tp .5s 1 ease '
      window.setTimeout(() => {
        document.body.removeChild(tips)
      }, 400)
    },
    enter (e) {
      console.log('进入事件')
    },
    getLocal (e) {
      console.log(e.pageX)
      console.log(e.pageY)
    }
  }
}
</script>

<style>
.output-warp {
cursor: pointer;
width: 462px;
height: 137px;
        padding: 10px 10px 43px;
        background-color: #fff;
        position: relative;
        border: 1px solid #c0c0c0;
        background: #c0c0c0;
        transition: all .3s;
}
.output-warp:hover{
  background: #acacac;
}
.context{
    text-align: left;
    border: 0px;
    top:8%;
    left:4%;
    width: 434px;
    height: 160px;
    font-size: 24px;
    line-height: 30px;
    position: absolute;
    white-space: pre-wrap;
    overflow-wrap: break-word;
    text-rendering: auto;
    display: inline-block;
}
@keyframes tp {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    display:none;
  }
}
</style>
