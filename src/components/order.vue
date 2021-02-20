<template>
  <div>
    <el-col :span="5">
      <div class="grid-content-goods bg-purple-dark-goods"></div>
    </el-col>
    <el-col :span="14">
      <div class="grid-content-goods bg-purple-dark-goods">
        <el-row>
          <div style="text-align: center">
            <img src="http://dfs.yun300.cn/group1/M00/15/A8/rBQBHFv2ZGKEPnmQAAAAAMvd6LE453.png"
                 style="width: 546px;height: 207px"
                 class="image">
          </div>
        </el-row>
        <el-row>
          <div style="text-align: center; padding: 10px;">
            <router-link to="/userInfo">尚未开发！</router-link>
          </div>
        </el-row>
      </div>
    </el-col>
    <el-col :span="5">
      <div class="grid-content-goods bg-purple-dark-goods"></div>
    </el-col>
  </div>
</template>
<style>
.bg-purple-dark-goods {
  background: Transparent;
}

.grid-content-goods {
  border-radius: 0px;
  min-height: 30px;
}
</style>
<script>
export default {
  data() {
    return {};
  },
  created() {
    this.initUserInfo();
  },
  methods: {
    // 界面进来就会根据localStorage存储的当前用户信息，初始化用户详情
    initUserInfo() {
      this.$message({
        showClose: true,
        message: '界面尚未开发'
      });
    }

  }
};
</script>
