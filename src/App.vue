<template>
  <div id="app">

    <el-row>
      <!--一个占位为5的空的content，自定义其背景色样式-->
      <el-col :span="5">
        <div class="grid-content bg-purple-dark"></div>
      </el-col>
      <el-col :span="14">
        <el-menu class="el-menu-demo" mode="horizontal" background-color="#1E89E0" text-color="#fff"
                 active-text-color="#ffd04b">
          <el-menu-item index="1">
            <router-link to="/userInfo">
              <el-button type="text">

                <img src="http://dfs.yun300.cn/group1/M00/15/A8/rBQBHFv2ZGKEPnmQAAAAAMvd6LE453.png"
                     style="width: 54px;height: 20px"
                     class="image">
                <!--                <img :src="'data:image/jpeg;base64,'+ demoUserImage" style="width: 42px;height: 42px">-->

              </el-button>
            </router-link>
          </el-menu-item>
          <el-menu-item index="2">
            <router-link to="/goods">人脸检测</router-link>
          </el-menu-item>
          <el-menu-item index="3">
            <router-link to="/message">安全帽检测</router-link>
          </el-menu-item>
          <el-menu-item index="4">
            <router-link to="/cart">行人检测</router-link>
          </el-menu-item>
          <!--          <el-menu-item index="5">-->
          <!--            <router-link to="/order">预留界面3</router-link>-->
          <!--          </el-menu-item>-->
        </el-menu>
      </el-col>
      <el-col :span="2">
        <el-menu class="el-menu-demo" mode="horizontal" background-color="#1E89E0" text-color="#fff"
                 active-text-color="#ffd04b">
          <el-menu-item index="7">
            <!--            <router-link to="/userInfo">登录/注册</router-link>-->
          </el-menu-item>
        </el-menu>
      </el-col>
      <el-col :span="3">
        <div class="grid-content bg-purple-dark"></div>
      </el-col>
    </el-row>


    <br>
    <router-view></router-view>

  </div>
</template>

<style>
a {
  /*去掉导航栏链接文字的下划线*/
  text-decoration: none;
  text-align: center;
}

/*样式的使用方式 .+标签 指到对应的标签*/
.el-menu {
  min-height: 60px;
  max-height: 60px;
}

.el-menu-item {
  min-height: 60px;
  max-height: 60px;
  /* 修改默认字体的大小 */
  font-size: 16px;
}

/* 两边填充位置的底色和el-menu-item el-menu保持一致 */
.bg-purple-dark {
  background: #1E89E0;
}

.grid-content {
  /* 圆角边框*/
  border-radius: 0px;
  /* 长度和el-menu-item el-menu在缩放的情况下保持一致*/
  min-height: 60px;
}
</style>

<script>
export default {
  created() {
    this.init();
  },
  data() {
    return {
      demoUserImage: '',

    };
  },
  methods: {
    init() {
      // // 当前无人，则请求guest，有人展示这个人的头像
      // if (localStorage.getItem('loginResult') === null) {
      //   this.initUserInfo();
      // } else {
      //   this.demoUserImage = JSON.parse(localStorage.getItem('loginResult')).user_image;
      // }
    },

    // // 清空当前登录信息，注入 guest 信息
    // initUserInfo() {
    //
    //   this.$http.put("getUserInfo", {
    //     user_id: 100001 // gust
    //   }).then(result => {
    //     let ret = result.body;
    //     if (ret.message === 'SUCCESS') {
    //
    //       localStorage.removeItem('loginResult');
    //       localStorage.setItem('loginResult', JSON.stringify(ret));
    //       this.demoUserImage = JSON.parse(localStorage.getItem('loginResult')).user_image;
    //
    //     } else {
    //       this.$message('服务器异常');
    //     }
    //   });
    //
    //
    // },


    // 占据末尾的function ，不会被调用，请在它上面添加functions ，
    useless_f() {
      this.$message({
        message: '道路畅通，随时可以开车',
        type: 'success'
      });
    }
  }
};
</script>