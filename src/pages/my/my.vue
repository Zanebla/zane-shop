<script setup lang="ts">
import { useMemberStore } from '@/stores'
import '@/utils/http'

const memberStore = useMemberStore()
// 测试请求函数
const getData = () => {
  uni.request({
    method: 'GET',
    url: '/home/banner',
    header: {},
  })
}
</script>

<template>
  <view class="my">
    <view>Member Information: {{ memberStore.profile }}</view>
    <button
      @tap="
        memberStore.setProfile({
          nickname: 'Zanebla',
          token: '12345',
        })
      "
      size="mini"
      plain
      type="primary"
    >
      Save User Information
    </button>
    <button @tap="memberStore.clearProfile()" size="mini" plain type="warn">清理用户信息</button>
    <button @tap="getData" size="mini" plain type="primary">测试请求</button>
  </view>
</template>

<style lang="scss">
//
</style>
