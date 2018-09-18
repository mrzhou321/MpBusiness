<template>
  <div>
    <div class="weui-flex">
      <div class="weui-flex__item">
        <swiper
          indicator-dots
          autoplay
        >
          <block
            v-for="(url, index) in imgUrls"
            :key="index"
          >
            <swiper-item>
              <image
                :src="url"
                class="slide-image"
              />
            </swiper-item>
            </block>
            </swiper>
      </div>
    </div>
    <div
      class="btn-area">
            <button
          open-type="openSetting"
        >设置</button>
        <button
          open-type="contact"
        >客服</button>
        <button
          open-type="getUserInfo"
          lang="zh_CN"
          bindgetuserinfo="onGotUserInfo"
        >信息</button>
  </div>
  <div class="weui-flex">
    <div class="weui-flex__item">
      <div class="placeholder">weui</div>
    </div>
    <div class="weui-flex__item">
      <div class="placeholder">weui</div>
    </div>
    <div class="weui-flex__item">
      <div class="placeholder">weui</div>
    </div>
    <div class="weui-flex__item">
      <div class="placeholder">weui</div>
    </div>
  </div>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      imgUrls: [
        'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
        'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
        'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg'
      ]
    }
  },

  components: {
    card
  },

  methods: {
    bindViewTap () {
      const url = '../logs/main'
      wx.navigateTo({ url })
    },
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    },
    clickHandle (msg, ev) {
      console.log('clickHandle:', msg, ev)
    }
  },

  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
  }
}
</script>

<style scoped>
.card {
  height: 200px;
}
.slide-image {
  width: 100%;
  height: 200px;
}
.btn-area {
 display: flex;
 justify-content: center;
 align-items: center;
 height: 100px;
 border: solid 1px black;
}
.btn-area button{
   background-color: blueviolet;
   width: 50px;
   height: 50px;
   border-radius: 50%;
   font-size: 12px;
   padding: 15px 0;
}
</style>
