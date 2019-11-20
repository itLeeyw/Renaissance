<template>
    <div class="output-warp">
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
  props: ['showContent']
}
</script>

<style>
.output-warp {

width: 462px;
height: 137px;
        padding: 10px 10px 43px;
        background-color: #fff;
        position: relative;
        border: 1px solid #ccc;
        background: #ccc;
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
    cursor: text;
    white-space: pre-wrap;
    overflow-wrap: break-word;
    text-rendering: auto;
    display: inline-block;
}
</style>
