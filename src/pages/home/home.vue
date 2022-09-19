<template>
	<view>
		首页： 用于显示梗概信息（Memo进度状态）
	</view>
  <view>Current DateTime: {{dt}}</view>
</template>

<script setup lang="ts">
  import {ref} from "vue";

  const dt = ref<String>();

  const get_basic_info = async () => {
    uni.request({
      url: "http://127.0.0.1:3000/basicinfo",
      dataType: "json",
      success: (res) => {
        dt.value = res.data.datetime;
      },
      fail: () => {
        dt.value = "FAILED"
      }
    })
  }

  setInterval(get_basic_info, 5000,)

  // uni.login({
  //   "provider": "weixin",
  //   "onlyAuthorize": true, // 微信登录仅请求授权认证
  //   success: function(event){
  //     console.log("UniApp.LoginRes: ", event)
  //     const {code} = event
  //     //客户端成功获取授权临时票据（code）,向业务服务器发起登录请求。
  //     uni.request({
  //       url: 'http://127.0.0.1:3000/loginByWeixin', //仅为示例，并非真实接口地址。
  //       data: {
  //         code: event.code
  //       },
  //       success: (res) => {
  //         //获得token完成登录
  //         uni.setStorageSync('token',res.token)
  //       }
  //     });
  //   },
  //   fail: function (err) {
  //     // 登录授权失败
  //     // err.code是错误码
  //     console.log("login failed:\n\t", err)
  //   }
  // })

</script>

<style lang="scss">

</style>
