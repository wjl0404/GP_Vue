<template>
  <div id="app">
    <nav class="navbar navbar-expand navbar-dark bg-dark">
      <router-link to="/" class="navbar-brand"
        >卡拉云_kalacloud.com</router-link
      >
      <div class="navbar-nav mr-auto">
        <li class="nav-item">
          <router-link :to="{
            path:'/todo'
          }"
            class="nav-link"
            >任务清单</router-link
          >
        </li>
        <li class="nav-item">
          <router-link :to="{
            path:'/add'
          }" class="nav-link">新增任务</router-link>
        </li>
      </div>
    </nav>

    <div class="container mt-3">
      <router-view />
    </div>

    <!-- <h2>add</h2> -->
  </div>
</template>

<script>
export default {
  name: "app",
  
};
</script>
