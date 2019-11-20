<template>
    <div class="trans-operation-wrapper clearfix">
        <div class="trans-operation clearfix">
            <a class="language-btn select-from-language"><span class="word">检测到中文</span></a>
            <a class="from-to-exchange language-btn"><span class="exchange-mask"></span></a>
            <a class="language-btn select-from-language"><span class="word">抽象话</span></a>
            <a class="trans-btn trans-btn-zh" @click="sendContent"></a>
        </div>
    </div>
</template>

<script>
export default {
  name: 'TOW',
  data () {
    return {
      isSend: false
    }
  },
  methods: {
    sendContent: function () {
      this.isSend = true
      this.$emit('sendContent', this.isSend)
      this.isSend = false
    }
  }
}
</script>
<style>
.trans-operation-wrapper{
    float: left;
    min-width: 670px;
    line-hight: 30px;
    font-size: 14px;
    margin-bottom: 5px;
}
.trans-operation{
    float: left;
    min-width: 670px;
}
.language-btn {
    display: inline-block;
    height: 30px;
    line-height: 30px;
    color: #333;
}
.select-from-language, .select-to-language {
    background: #fff;
    border: 1px solid #dcdcdc;
    border-radius: 5px;
    width: 176px;
    text-align: center;
}
.trans-operation a{
    float: left;
    text-decoration: none;
}
.clearfix:before, clearfix:after{
    content: " ";
    display: table;
}
.clearfix:after{
    clear: both;
}
.word {
    cursor: pointer;
}

.exchange-mask{
    display: inline-block;
    width: 21px;
    height: 21px;
    overflow: hidden;
    background-image: url(../assets/zh.png);
    background-repeat: no-repeat;
    vertical-align: middle;
    margin-top: -4px;
    background-position: 4px 50%;
}
.from-to-exchange {
    padding: 0 21px;
    height: 30px;
    line-height: 30px;
    background-color: #f9f9f9;
}
.language-btn{
    display: inline-block;
    color: #333;
}
.trans-btn-zh {
    width: 106px;
    height: 32px;
    border: 0;
    padding: 0;
    text-align: center;
    text-indent: 18px;
    letter-spacing: 18px;
    font-weight: 400;
    background-color: #4395ff;
    font-size: 14px;
    text-decoration: none!important;
}
.trans-btn{
    cursor: pointer;
    display: inline-block;
    color: #fff;
    margin-left: 14px;
    border-radius: 5px;
    line-height: 30px;
    vertical-align: top;
    transtion:all .2s ease-in;
}
.trans-btn:hover{
    background-color: #0064FF;
}
.trans-btn-zh::after {
    content: "翻译";
    color: rgb(255, 255, 255);
    line-height: 32px;
}
</style>
