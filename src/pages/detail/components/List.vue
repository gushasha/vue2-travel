<template>
  <div>
    <div v-for="n of 4" :key="n">
      <div class="hr-border"></div>
      <div class="panel">
        <div class="panel-title border-bottom">
          <span class="panel-title-icon"></span>
          <span class="panel-title-text">热销联票</span>
        </div>
        <div class="panel-content">
          <div
              class="panel-content-item border-bottom"
              v-for="item of hotList"
              :key="item.id"
          >
            <div class="panel-content-item-title">{{ item.title }}</div>
            <div class="mp-ticket-type-price mp-price">
              ¥
              <em class="mp-price-num">{{ item.price }}</em>
              <span class="mp-ticket-numword">起</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default{
  name: 'DetailList',
  data () {
    return {
      hotList: [
        {
          id: 1,
          title: '【成都出发】成都-青城山/都江堰直通车（可选门票套餐）',
          price: 176
        }, {
          id: 2,
          title: '【成都出发】青城山+都江堰高品质一日游',
          price: 10.01
        }, {
          id: 3,
          title: '都江堰+青城山成人联票',
          price: 380
        }
      ]
    }
  },
  props: {
    categoryList: Array
  }
}
</script>

<style scoped>
.hr-border {
  height: .2rem;
  background: #e8e8e8;
}
.panel {
  padding: 0 .2rem;
}
  .panel-title {
    position: relative;
    height: .8rem;
  }
    .panel-title-text {
      font-size: .34rem;
      margin-left: .4rem;
      height: .8rem;
      line-height: .8rem;
    }
    .panel-title-icon {
      position: absolute;
      top: .22rem;
      width: .36rem;
      height: .36rem;
      background: url(//s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat;
      background-size: .4rem 3rem;
    }
  .panel-content {}
    .panel-content-item {
      display: flex;
      flex-direction: row;
      justify-content: space-around;
      align-items: center;
    }
      .panel-content-item-title {
        flex: 1;
        padding: .2rem 0;
        font-size: .3rem;
        line-height: .4rem;
      }
      .mp-ticket-type-price {
        padding: .2rem 0;
        color: darkorange;
      }
        .mp-price-num {
          font-size: .42rem;
        }
        .mp-ticket-numword {
          color: #9e9e9e;
          font-size: .24rem;
        }
</style>
