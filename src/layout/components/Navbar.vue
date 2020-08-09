<template>
  <div class="navbar">
    <hamburger id="hamburger-container" :is-active="sidebar.opened" class="hamburger-container" @toggleClick="toggleSideBar" />
    
    <!-- <breadcrumb id="breadcrumb-container" class="breadcrumb-container" /> -->
    
    <ul class="nav">
      <li>模块</li>
      <li>人员</li>
      <li>集成</li>
      <li>对接</li>
      <li>案例</li>
      <li>流转</li>
      <li>事项</li>
    </ul>
   
     <div class="search">
        <div class="search_box"> 
           <i class="el-icon-search"></i>
            <input type="text" class="search_input" placeholder="输入搜索名称" />
         </div>
        <input type="button"  value="搜索" class="search_btn"/>
    </div>
    
    <div class="member">
        <el-avatar icon="el-icon-user-solid" :size="25"></el-avatar>
        <span style="padding-top:5px;">张三</span>
    </div>
    <div class="login_out fr">  <i class="el-icon-switch-button"></i></div>
    
<!--     
    <div class="right-menu"> -->
      <!-- <template v-if="device!=='mobile'"> -->
        <!-- <search id="header-search" class="right-menu-item" /> -->

        <!-- <error-log class="errLog-container right-menu-item hover-effect" /> -->

        <!-- <screenfull id="screenfull" class="right-menu-item hover-effect" /> -->

        <!-- <el-tooltip content="Global Size" effect="dark" placement="bottom">
          <size-select id="size-select" class="right-menu-item hover-effect" />
        </el-tooltip> -->

      <!-- </template> -->

      <!-- <el-dropdown class="avatar-container right-menu-item hover-effect" trigger="click">
        <div class="avatar-wrapper">
          <img :src="avatar+'?imageView2/1/w/80/h/80'" class="user-avatar">
          <i class="el-icon-caret-bottom" />
        </div>
        <el-dropdown-menu slot="dropdown">
          <router-link to="/profile/index">
            <el-dropdown-item>Profile</el-dropdown-item>
          </router-link>
          <router-link to="/">
            <el-dropdown-item>Dashboard</el-dropdown-item>
          </router-link>
          <a target="_blank" href="https://github.com/PanJiaChen/vue-element-admin/">
            <el-dropdown-item>Github</el-dropdown-item>
          </a>
          <a target="_blank" href="https://panjiachen.github.io/vue-element-admin-site/#/">
            <el-dropdown-item>Docs</el-dropdown-item>
          </a>
          <el-dropdown-item divided @click.native="logout">
            <span style="display:block;">Log Out</span>
          </el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown> -->
    <!-- </div> -->
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import Breadcrumb from '@/components/Breadcrumb'
import Hamburger from '@/components/Hamburger'
// import ErrorLog from '@/components/ErrorLog'
// import Screenfull from '@/components/Screenfull'
// import SizeSelect from '@/components/SizeSelect'
// import Search from '@/components/HeaderSearch'

export default {
  components: {
    Breadcrumb,
     Hamburger,
    // ErrorLog,
    // Screenfull,
    // SizeSelect,
    // Search
  },
  computed: {
    ...mapGetters([
      'sidebar',
      'avatar',
      'device'
    ])
  },
  methods: {
    toggleSideBar() {
      this.$store.dispatch('app/toggleSideBar')
    },
    async logout() {
      await this.$store.dispatch('user/logout')
      this.$router.push(`/login?redirect=${this.$route.fullPath}`)
    }
  }
}
</script>

<style lang="scss" scoped>

.nav{ float: left;  padding-top:15px; padding-left: 0;  padding-right: 5%;}
.nav li{ float: left; font-size: 16px; color: #fff; padding: 0 25px; font-weight: bold;}
.search{ float:left;margin-top: 20px; width: 355px;  margin-right: 5%;}
.search_box{ width:298px; border: 1px solid #8aa4da; height: 38px; border-radius: 5px; float: left; }
.search i{color: #fff;margin: 8px 10px 0 13px;}
.search_input{ border:none; background:none;outline:none; color: #fff; }
.search_btn{float: left; border:none; background:none; color: #fff; outline:none; cursor: pointer; margin-top:8px; margin-left:5px;  }
.member{ float:left; margin-top:25px; color: #fff;}
.member span{ display: inline-block; float: left; margin-left: 8px;}
.login_out{ padding-top: 25px; padding-right: 20px;}

.login_out i{ height: 30px;width:30px; color: #fff;font-size:30px;}








.navbar {
  height: 80px;
  overflow: hidden;
  position: relative;
  background: #2f66cc;
  box-shadow: 0 1px 4px rgba(0,21,41,.08);

  .hamburger-container {
    line-height: 46px;
    margin-top: 15px;

    height: 100%;
    float: left;
    cursor: pointer;
    transition: background .3s;
    -webkit-tap-highlight-color:transparent;

    &:hover {
      background: rgba(0, 0, 0, .025)
    }
  }

  .breadcrumb-container {
    margin-top: 15px;
    color: #fff;
    float: left;
  }

  .errLog-container {
    display: inline-block;
   
    vertical-align: top;
  }

  .right-menu {
    float: right;
    height: 100%;
    line-height: 50px;

    &:focus {
      outline: none;
    }

    .right-menu-item {
      display: inline-block;
      padding: 0 8px;
      height: 100%;
      font-size: 18px;
      color: #5a5e66;
      vertical-align: text-bottom;

      &.hover-effect {
        cursor: pointer;
        transition: background .3s;

        &:hover {
          background: rgba(0, 0, 0, .025)
        }
      }
    }

    .avatar-container {
      margin-right: 30px;

      .avatar-wrapper {
        margin-top: 5px;
        position: relative;

        .user-avatar {
          cursor: pointer;
          width: 40px;
          height: 40px;
          border-radius: 10px;
        }

        .el-icon-caret-bottom {
          cursor: pointer;
          position: absolute;
          right: -20px;
          top: 25px;
          font-size: 12px;
        }
      }
    }
  }
}
</style>
