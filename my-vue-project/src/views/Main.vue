<template>
  <div id="Main">
    <el-container style="height:auto; border: 1px solid #eee">
      <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
        <el-menu
          router
          v-for="menu in menuitem"
          :key="menu.index"
          default-active="1-1"
          @open="handleOpen"
          @close="handleClose"
        >
          <el-submenu :index="menu.index">
            <template slot="title">
              <i></i>
              <span>{{ menu.text }}</span>
            </template>

            <el-menu-item
              v-for="child in menu.children"
              :key="child.index"
              :route="{ path: child.link }"
              :index="child.index"
              >{{ child.text }}
            </el-menu-item>
          </el-submenu>
          <!-- <el-submenu index="2">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>导航二</span>
        </template>
          <el-menu-item index="3-1">选项1</el-menu-item>
          <el-menu-item index="2-2">选项2</el-menu-item>
          <el-menu-item index="2-3">选项3</el-menu-item>
      </el-submenu> -->
        </el-menu>
      </el-aside>
      <el-main style="width:1024px">
        <router-view />
      </el-main>
    </el-container>
  </div>
</template>

<script>
export default {
  name: "Main",
  data() {
    return {
      menuitem: [
        {
          index: "1",
          text: "导航一",
          children: [
            {
              index: "1-1",
              text: "选项1",
              link: "/home",
            },
            {
              index: "1-2",
              text: "选项2",
              link: "/about",
            },
          ],
        },
      ],
    };
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },
  },
};
</script>

