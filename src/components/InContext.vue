<template>
    <div class="input-warp">
        <textarea v-model="content" class="context" style="height: 70px; overflow: hidden;" :placeholder=msg >

        </textarea>
    </div>
</template>

<script>
export default {
  name: 'InContext',
  data () {
    return {
      msg: '人人都笑孙笑川，人人都是孙笑川',
      content: ''
    }
  },
  watch: {
    'content': function (newVal, oldVal) {
      this.$emit('getContent', newVal)
    }
  }
}
</script>

<style scoped>

.input-warp {
        width: 462px;
        height: 137px;
        padding: 10px 10px 43px;
        background-color: #fff;
        position: relative;
        border: 1px solid #ccc;
    }
.context{
        border: 0px;
        width: 434px;
        top:8%;
        left:4%;
        font-size: 24px;
        line-height: 30px;
        position: absolute;
        background-color: transparent;
        resize: none;
        cursor: text;
        white-space: pre-wrap;
      overflow-wrap: break-word;
          text-rendering: auto;
          display: inline-block;
    }
</style>
