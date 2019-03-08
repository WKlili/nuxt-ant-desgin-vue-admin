<template>
  <a-layout id="layout-trigger">
    <a-layout-sider
      :trigger="null"
      v-model="collapsed"
      class="SiderMenu"
      collapsible
    >
      <div class="logo">
        <a-tooltip placement="rightTop">
          <template slot="title">
            <span>admin</span>
          </template>
          <span
            v-if="!collapsed"
            class="textOverflow"
          >
            admin
          </span>
        </a-tooltip>
      </div>
      <a-menu :defaultSelectedKeys="['1']" theme="dark" mode="inline">
        <a-menu-item key="1">
          <a-icon type="user" />
          <span>nav 1</span>
        </a-menu-item>
        <a-menu-item key="2">
          <a-icon type="video-camera" />
          <span>nav 2</span>
        </a-menu-item>
        <a-menu-item key="3">
          <a-icon type="upload" />
          <span>nav 3</span>
        </a-menu-item>
      </a-menu>
    </a-layout-sider>
    <a-layout>
      <a-layout-header style="background: #fff; padding: 0">
        <a-icon
          :type="collapsed ? 'menu-unfold' : 'menu-fold'"
          @click="()=> collapsed = !collapsed"
          class="trigger"
        />
      </a-layout-header>
      <a-layout-content class="outer-container">
        <div class="inner-container">
          <nuxt />
        </div>
      </a-layout-content>
    </a-layout>
  </a-layout>
</template>

<script>
export default {
  data() {
    return {
      collapsed: false
    }
  }
}
</script>

<style scoped>
#layout-trigger {
  width: 100%;
  height: 100%;
}

#layout-trigger .SiderMenu {
  height: 100vh;
}

#layout-trigger .outer-container {
  position: relative;
  margin: 0 16px;
  min-height: 300px;
  padding-top: 16px;
  overflow: hidden;
}

#layout-trigger .inner-container {
  position: absolute;
  left: 0;
  top: 16px;
  right: -17px;
  bottom: 0;
  overflow-x: hidden;
  overflow-y: scroll;
}

.logo {
  display: flex;
  justify-content: center;
  background-color: #002140;
  height: 64px;
  padding: 2px 16px;
  color: #ffffff;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.logo img {
  height: 100%;
}

.logo span {
  height: 100%;
  text-indent: 10px;
}

.logo span {
  font-size: 20px;
}

.textOverflow {
  width: 10em;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

#layout-trigger .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color 0.3s;
}

#layout-trigger .trigger:hover {
  color: #1890ff;
}

#layout-trigger .logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px;
}
</style>
