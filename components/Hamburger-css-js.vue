<template>
  <div v-if="$route.path == '/'" class="hamburger">
    <div class="openbtn" :class="{active: active}" @click="toggleMenu()">
      <span /><span /><span />
    </div>
    <nav id="g-nav" :class="{panelactive: panelactive}">
      <div id="g-nav-list">
        <!--ナビの数が増えた場合縦スクロールするためのdiv※不要なら削除-->
        <ul>
          <li @click="toggleMenu()">
            <nuxt-link v-scroll-to="toNews" to="/">
              トップ
            </nuxt-link>
          </li>
          <li @click="toggleMenu()">
            <nuxt-link v-scroll-to="toAbout" to="/">
              DJ一覧
            </nuxt-link>
          </li>
          <li @click="toggleMenu()">
            <nuxt-link v-scroll-to="toWorks" to="/">
              使い方
            </nuxt-link>
          </li>
          <li @click="toggleMenu()">
            <nuxt-link v-scroll-to="toProfile" to="/">
              メディア
            </nuxt-link>
          </li>
          <li @click="toggleMenu()">
            <nuxt-link v-scroll-to="toMembers" to="/">
              講師DJ募集
            </nuxt-link>
          </li>
        </ul>
      </div>
    </nav>
    <div class="circle-bg" :class="{circleactive: circleactive}" />
  </div>
</template>

<script>
export default {
  data () {
    return {
      active: false,
      panelactive: false,
      circleactive: false,
      toTop: '#main-visual',
      toNews: '#news-container',
      toAbout: '#about',
      toWorks: '#works-container',
      toProfile: '#company-profile',
      toMembers: '#members',
      toContact: '#contact'
    }
  },
  methods: {
    toggleMenu () {
      if (!this.active) {
        this.active = true
        this.panelactive = true
        this.circleactive = true
      } else {
        this.active = false
        this.panelactive = false
        this.circleactive = false
      }
    }
  }
}
</script>

<style scoped>
/*========= ナビゲーションのためのCSS ===============*/
/*アクティブになったエリア*/
#g-nav.panelactive{
  /*position:fixed;にし、z-indexの数値を大きくして前面へ*/
  width:100%;
  position:fixed;
  z-index: 999;
  top: 0;
  right: 0;
  height: 100vh;
}
/*丸の拡大*/
.circle-bg{
  position: fixed;
  z-index:3;
  /*丸の形*/
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: #ffffff;
  /*丸のスタート位置と形状*/
  transform: scale(0);/*scaleをはじめは0に*/
  right: 0px;
  top: 0px;
  transition: all .6s;/*0.6秒かけてアニメーション*/
}
.circle-bg.circleactive{
  transform: scale(50);/*クラスが付与されたらscaleを拡大*/
}
/*ナビゲーションの縦スクロール*/
#g-nav-list{
  display: none;/*はじめは表示なし*/
  /*ナビの数が増えた場合縦スクロール*/
  position: fixed;
  z-index: 999;
  width: 100%;
  height: 100vh;
  overflow: auto;
  -webkit-overflow-scrolling: touch;
}
#g-nav.panelactive #g-nav-list{
  display: block; /*クラスが付与されたら出現*/
}
/*ナビゲーション*/
#g-nav ul {
  opacity: 0;/*はじめは透過0*/
  /*ナビゲーション天地中央揃え※レイアウトによって調整してください。不必要なら削除*/
  position: absolute;
  z-index: 999;
  top:50%;
  left:50%;
  transform: translate(-50%,-50%);
}
/*背景が出現後にナビゲーションを表示*/
#g-nav.panelactive ul {
  opacity:1;
}
/* 背景が出現後にナビゲーション li を表示※レイアウトによって調整してください。不必要なら削除*/
#g-nav.panelactive ul li{
  animation-name:gnaviAnime;
  animation-duration:1s;
  animation-delay:.2s;/*0.2 秒遅らせて出現*/
  animation-fill-mode:forwards;
  opacity:0;
}
@keyframes gnaviAnime{
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
/*リストのレイアウト設定*/
#g-nav li{
  text-align: center;
  list-style: none;
}
#g-nav li a{
  color: #333;
  text-decoration: none;
  padding:10px;
  display: block;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  font-weight: bold;
}
/*========= ボタンのためのCSS ===============*/
.openbtn{
  position:relative;
  right: 0px;
  z-index: 9999;/*ボタンを最前面に*/
  cursor: pointer;
  width: 50px;
  height:50px;
  background-color: #f77474;
  border-radius: 50%;
}

/*×に変化*/
.openbtn span{
  display: inline-block;
  transition: all .4s;
  position: absolute;
  left: 13px;
  height: 3px;
  border-radius: 2px;
  background-color: #ffffff;
  width: 50%;
}

.openbtn span:nth-of-type(1) {
  top:15px;
}
.openbtn span:nth-of-type(2) {
  top:23px;
}
.openbtn span:nth-of-type(3) {
  top:31px;
}
.openbtn.active span:nth-of-type(1) {
  top: 18px;
  left: 18px;
  transform: translateY(6px) rotate(-45deg);
  width: 30%;
}
.openbtn.active span:nth-of-type(2) {
  opacity: 0;
}
.openbtn.active span:nth-of-type(3){
  top: 30px;
  left: 18px;
  transform: translateY(-6px) rotate(45deg);
  width: 30%;
}

@media screen and (max-width: 400px) {
  .openbtn{
    width: 40px;
    height: 40px;
    right: 5px;
  }
  .openbtn span{
    left: 10px;
  }
  .openbtn span:nth-of-type(1) {
    top: 12px;
  }
  .openbtn span:nth-of-type(2) {
    top: 19px;
  }
  .openbtn span:nth-of-type(3) {
    top: 26px;
  }
  .openbtn.active span:nth-of-type(1) {
    top: 18px;
    left: 15px;
    transform: translateY(0px) rotate(-45deg);
    width: 30%;
  }
  .openbtn.active span:nth-of-type(3){
    top: 30px;
    left: 15px;
    transform: translateY(-12px) rotate(45deg);
    width: 30%;
  }
}
</style>
