
<template>
    <div class="btm-warp">
        <p class="btm-top">
            <a @click="AddFavorite()">收藏本站</a>
            <a>关于本站</a>
            <a href ="http://wpa.qq.com/msgrd?v=3&uin=2621847675&site=qq&menu=yes" target="_blank">联系站主</a>
            <span>欢迎交流学习</span>
        </p>
        <p class="btm-btm">
            © Leeyw
            <a href="https://github.com/itLeeyw/Renaissance" target="_blank" class="star">
                <div class="star-warp">
                    <div class="star-l">
                        <img src="../assets/star.png" />
                        star
                    </div>
                    <div class="star-r">
                        1k
                    </div>
                </div>
            </a>
        </p>
    </div>
</template>
<script>
export default{
  name: 'bottom',
  methods: {
    AddFavorite () {
      let title = '文艺复兴'
      let url = location.href
      console.log(url)
      try {
        window.external.addFavorite(url, title)
      } catch (e) {
        try {
          window.sidebar.addPanel(title, url, '')
        } catch (e) {
          alert('抱歉，您所使用的浏览器无法完成此操作。\n\n加入收藏失败，请使用Ctrl+D进行添加')
        }
      }
    }
  }
}
</script>

<style>
.btm-warp{
    color: #808080;
    font-size: 12px;
}
.btm-top{
    margin-bottom: 10px;
}
.btm-top a,
.btm-top span,
.btm-btm a{
    cursor: pointer;
    margin-left: 25px;
}
.btm-btm a{
    text-decoration: none;
}
.star{
    align-text: center;
    background: rgb(232,237,242);
    border-radius: 3px;
    border:1px solid #ccc;
    display:inline-block;
    width:80px;
    height:24px;
    line-height: 24px;
}
.star-warp{
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}
.star-l{
    height:100%;
    flex: 2;
    border:1px solid #ccc;
}
.star-r{
    height:100%;
    flex: 1;
    background: white;
    border:1px solid #ccc;
}
</style>
