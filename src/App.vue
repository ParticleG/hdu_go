<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-primary text-white" height-hint="98">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="drawerOpen = !drawerOpen"/>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg">
          </q-avatar>
          HDU GO
        </q-toolbar-title>
      </q-toolbar>
      <q-tabs align="left">
        <q-route-tab to="/page1" label="Page One"/>
        <q-route-tab to="/page2" label="Page Two"/>
        <q-route-tab to="/page3" label="Page Three"/>
      </q-tabs>
    </q-header>
    <q-drawer show-if-above v-model="drawerOpen" side="left" elevated>
      <q-list>
        <q-item-label header>选项菜单</q-item-label>
        <q-item clickable tag="a" target="_blank" href="https://quasar.dev">
          <q-item-section avatar>
            <q-icon name="dashboard"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>仪表盘</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" target="_blank" href="https://github.com/quasarframework/">
          <q-item-section avatar>
            <q-icon name="school"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>网上选课</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" target="_blank" href="https://chat.quasar.dev">
          <q-item-section avatar>
            <q-icon name="info"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>信息查询</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <!--<router-view/>-->
      <HelloWorld/>
    </q-page-container>

  </q-layout>
</template>

<style>
</style>

<script>
import HelloWorld from './components/HelloWorld.vue'
import {Dark} from 'quasar'

// 获得状态
console.log(Dark.isActive)

// 获取配置状态
console.log(Dark.mode) // "auto", true, false

// 设置状态
Dark.set(true) // 或者false或者"auto"

// 切换
Dark.toggle()

export default {
  name: 'LayoutMain',
  components: {
    HelloWorld
  },
  data() {
    return {
      drawerOpen: false
    }
  }
}
</script>
