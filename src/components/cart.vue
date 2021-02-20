<template>
  <div>


    <el-col :span="1">
      <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
    </el-col>
    <el-col :span="22">
      <div class="grid-content-userInfo bg-purple-dark-userInfo">

        <el-col :span="20" class="grid">

          <el-row>
            <el-col :span="5">
              <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
            </el-col>
            <el-col :span="14">

              <div class="grid-content-userInfo bg-purple-dark-userInfo">
                <div class="demo-img-userPhoto" v-if="pic_default">
                  <img src="http://dfs.yun300.cn/group1/M00/15/A8/rBQBHFv2ZGKEPnmQAAAAAMvd6LE453.png"
                       style="width: 640px; margin-top: 50px"
                       class="image">
                </div>
              </div>

              <div class="demo-img-userPhoto" v-if="pic_area_h">
                <div style="position: relative;">
                  <div style="position: absolute;" v-if="show_warning">
                    <img src="../assets/002.gif" style="width: 320px; margin-top: 20px; margin-left: 150px"/>
                  </div>
                  <img :src="'data:image/jpeg;base64,'+ flow_img_h"
                       style="width: 640px;height: 480px; margin-right: 200px"></img>
                </div>


              </div>


              <div class="demo-img-userPhoto2" v-if="stop_pic_area_h">
                <img :src="'data:image/jpeg;base64,'+ stop_flow_img_h"
                     style="width: 640px;height: 480px; margin-right: 200px"></img>
              </div>


            </el-col>
            <el-col :span="5">
              <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="5">
              <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
            </el-col>
            <el-col :span="14">
              <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="5">
              <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
            </el-col>
            <el-col :span="14">
              <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="5">
              <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
            </el-col>
            <el-col :span="14">
              <div class="grid-content-userInfo bg-purple-dark-userInfo">
                <div class="demo-button-signInOut" style="margin-top: 10px;">
                  <el-button type="primary" style="margin: 5px" @click.prevent="start_detc()">检测(行人)</el-button>
                  <el-button type="primary" style="margin: 5px" @click.prevent="stop_detc()">暂停</el-button>
                </div>

              </div>
            </el-col>
            <el-col :span="5">
              <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
            </el-col>
          </el-row>


        </el-col>
        <el-col :span="4" class="grid">
        </el-col>


      </div>
    </el-col>
    <el-col :span="1">
      <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
    </el-col>


    <el-col :span="5">
      <div class="grid-content-goods bg-purple-dark-goods">


      </div>
    </el-col>
    <el-col :span="14">
      <div class="grid-content-goods bg-purple-dark-goods">
        <!--视频显示框-->
        <el-col :span="18" class="grid">


        </el-col>

      </div>
    </el-col>
    <el-col :span="5">
      <div class="grid-content-goods bg-purple-dark-goods">


      </div>
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

/*搜索行，样式全局影响，要特殊命名*/
.bg-purple-dark-userInfo {
  background: Transparent;
}

.grid-content-userInfo {
  border-radius: 0px;
  min-height: 30px;
}

.bg-purple-dark-goods {
  background: Transparent;
}

.grid-content-goods {
  border-radius: 0px;
  min-height: 30px;
}

.bg-purple-dark-goods2 {
  background: #E5E5E5;
}

.grid-content-goods2 {
  border-radius: 0px;
  min-height: 100px;
}
</style>
<script>
export default {
  data() {
    return {
      pic_area_h: false,
      stop_pic_area_h: false,
      pic_default: true,
      websocket_linked: false,
      show_warning: false,

      flow_img_h: '',
      stop_flow_img_h: '',

    };
  },
  created() {
    this.init();
  },
  methods: {
    // 界面进来就会根据localStorage存储的当前用户信息，初始化用户详情
    init() {

    },

    runSocket() {
      this.ws = new WebSocket("ws://10.20.35.134:5680/");
      // this.ws = new WebSocket("ws://10.20.50.163:5680/");
      // this.ws = new WebSocket("ws://10.20.40.68:5680/");
      this.ws.onopen = this.websocketonopen;
      this.ws.onerror = this.websocketonerror;
      this.ws.onmessage = this.websocketonmessage;
      this.ws.onclose = this.websocketclose;
    },

    // 定义 websocket open属性的函数
    websocketonopen: function () {
      this.$message({
        message: '服务器连接成功...',
        type: 'success'
      });
      this.pic_default = false;
      this.websocket_linked = true
    },
    // 定义 websocket onerror属性的函数
    websocketonerror: function (e) {
      console.log('WebSocket_hat 连接发生错误');
    },
    // 定义 websocket onmessage属性的函数
    websocketonmessage: function (e) {
      let result = JSON.parse(e.data);
      if (result.message === 'SUCCESS') {
        this.flow_img_h = result.image;
        if (result.flag) {
          this.show_warning = true;
        } else {
          this.show_warning = false;
        }


      } else {
      }
    },
    // 定义 websocket onclose属性的函数
    websocketclose: function (e) {
      this.$message({
        message: '服务器连接关闭了...',
        type: 'success'
      });
      this.pic_default = true;
      this.pic_area_h = false;
      this.stop_pic_area_h = false;
    },

    start_detc() {
      this.pic_area_h = true;
      this.stop_pic_area_h = false;
      this.runSocket();

    },
    stop_detc() {
      this.pic_area_h = false;
      this.stop_pic_area_h = true;
      this.stop_flow_img_h = this.flow_img_h;
    },


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
