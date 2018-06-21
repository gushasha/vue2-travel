<template>
  <div>
    <div class="banner-wrapper" @click="handleClickBanner">
      <img class="banner-img" :src="bannerImg">
      <div class="banner-info">
        <div class="banner-title">
          <span>{{ sightName }}</span>
        </div>
        <div class="banner-number">
          <span class="icon iconfont banner-icon">&#xe600;</span>
          <span>42</span>
        </div>
      </div>
    </div>
    <common-fade-animation>
      <common-gallery
          :imgs="galleryImgs"
          v-show="showGallery"
          @close="HandleGalleryClose"
      ></common-gallery>
    </common-fade-animation>
    <div class="description border-bottom">
      <div class="description-top-left border-right">
        <div class="desc-score-info">
          <span class="desc-score-number">4.9分</span>
          <span>很棒</span>
        </div>
        <div class="desc-comment-info">10980条评论&emsp;59个攻略</div>
      </div>
      <div class="description-top-right">
        <div class="description-top-right-title">景点简介</div>
        <div class="description-top-right-text">开放时间、贴士</div>
      </div>
    </div>
    <div class="description-bottom">
      <div>四川省成都市都江堰市青城山路</div>
    </div>
  </div>
</template>

<script>
import CommonGallery from 'common/gallery/Gallery'
import CommonFadeAnimation from 'common/fade/FadeAnimation'

export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    galleryImgs: Array
  },
  data () {
    return {
      showGallery: false
    }
  },
  methods: {
    handleClickBanner () {
      this.showGallery = true
    },
    HandleGalleryClose () {
      this.showGallery = false
    }
  },
  components: {
    CommonGallery,
    CommonFadeAnimation
  }
}
</script>

<style lang="stylus" scoped>
.banner-wrapper {
  height: 0;
  padding-bottom: 55%;
  overflow: hidden;
  background: #000;
  position: relative;
}
  .banner-img {
    width: 100%;
  }
  .banner-info {
    position: absolute;
    left: 0;
    right: .2rem;
    bottom: 0;
    color: #fff;
    line-height: .64rem;
    display: flex;
    background-image: linear-gradient(rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8));
  }
    .banner-title {
      flex: 1;
      font-size: .32rem;
      padding: 0 .2rem;
    }
    .banner-number {
      line-height: .4rem;
      height: .4rem;
      margin-top: .12rem;
      padding: 0 .32rem;
      background: rgba(0,0,0,.5); /* 设置带透明度的背景色 */
      border-radius: .2rem;
      font-size: .2rem;
    }
      .banner-icon {
        font-size: .2rem;
      }
.description {
  display: flex;
}
  .description-top-left {
    flex: 1;
    margin: .3rem .5rem;
  }
    .desc-score-info {
      color: darkorange;
      font-size: .3rem;
    }
      .desc-score-number {
        font-size: .4rem;
      }
    .desc-comment-info {
      margin-top: .1rem;
      color: #9e9e9e;
      font-size: .24rem;
    }
  .description-top-right {
    margin: .3rem .3rem;
  }
    .description-top-right-title {
      font-size: .34rem;
    }
    .description-top-right-text {
      margin-top: .1rem;
      color: #9e9e9e;
      font-size: .24rem;
    }
.description-bottom {
  height: .4rem;
  line-height: .4rem;
  margin: .3rem .5rem;
  font-size: .28rem;
}
</style>
