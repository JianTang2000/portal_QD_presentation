<!--这个界面用来：在用户d登录之后，展示视频流-->


<template>
  <div>
    <el-row>
      <el-col :span="1">
        <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
      </el-col>
      <el-col :span="22">
        <div class="grid-content-userInfo bg-purple-dark-userInfo">
          <!--左边-->
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
              </el-col>
              <el-col :span="5">
                <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
              </el-col>
            </el-row>

            <el-row>
              <el-col :span="12">
                <div class="grid-content-userInfo bg-purple-dark-userInfo">
                  <div class="demo-img-userPhoto" v-if="pic_area">
                    <img :src="'data:image/jpeg;base64,'+ flow_img"
                         style="width: 500px;height: 375px; margin: 20px"></img>
                  </div>
                </div>
              </el-col>
              <el-col :span="12">
                <div class="grid-content-userInfo bg-purple-dark-userInfo">
                  <div class="demo-img-userPhoto3" v-if="pic_area_key">
                    <img :src="'data:image/jpeg;base64,'+ flow_img_key"
                         style="width: 500px;height: 375px; margin: 20px"></img>
                  </div>
                </div>
              </el-col>
            </el-row>

            <el-row>
              <el-col :span="12">
                <div class="grid-content-userInfo bg-purple-dark-userInfo">
                  <div class="demo-img-userPhoto2" v-if="stop_pic_area">
                    <img :src="'data:image/jpeg;base64,'+ stop_flow_img"
                         style="width: 500px;height: 375px; margin: 20px"></img>
                  </div>
                </div>
              </el-col>
              <el-col :span="12">
                <div class="grid-content-userInfo bg-purple-dark-userInfo">
                  <div class="demo-img-userPhoto2" v-if="stop_pic_area_key">
                    <img :src="'data:image/jpeg;base64,'+ stop_flow_img_key"
                         style="width: 500px;height: 375px; margin: 20px"></img>
                  </div>
                </div>
              </el-col>
            </el-row>


            <el-row>
              <el-col :span="5">
                <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
              </el-col>
              <el-col :span="14">
                <div class="grid-content-userInfo bg-purple-dark-userInfo">

                  <div class="demo-button-signInOut" style="margin-top: 10px;">
                    <el-button type="primary" style="margin: 5px" @click.prevent="openSignUp()">上传</el-button>
                    <el-button type="primary" style="margin: 5px" @click.prevent="start_detc()">检测</el-button>
                    <el-button type="primary" style="margin: 5px" @click.prevent="stop_detc()">暂停</el-button>
                  </div>


                </div>
              </el-col>
              <el-col :span="5">
                <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
              </el-col>
            </el-row>


          </el-col>


          <!--右边 -->
          <el-col :span="4" class="grid">

            <el-row v-if="pic_info_area_s2" style="margin-top: 80px">
              <div class="demo-input-email" style="margin-top: 10px;">
                <el-row :gutter="2">
                  <el-col :span="12">
                    <div style="text-align: right">
                      检测到人数 :
                    </div>
                  </el-col>
                  <el-col :span="12">
                    <el-input
                        :disabled="false"
                        style="margin-top: -6px;"
                        type="textarea"
                        autosize
                        v-model="textArea_user_num">
                    </el-input>
                  </el-col>
                </el-row>
              </div>

              <div class="demo-input-email" style="margin-top: 10px;">
                <el-row :gutter="2">
                  <el-col :span="12">
                    <div style="text-align: right">
                      姓名 :
                    </div>
                  </el-col>
                  <el-col :span="12">
                    <el-input
                        :disabled="false"
                        style="margin-top: -6px;"
                        type="textarea"
                        autosize
                        v-model="textArea_user_name1">
                    </el-input>
                  </el-col>
                </el-row>
              </div>

              <div class="demo-input-email" style="margin-top: 10px;">
                <el-row :gutter="2">
                  <el-col :span="12">
                    <div style="text-align: right">
                      工号 :
                    </div>
                  </el-col>
                  <el-col :span="12">
                    <el-input
                        :disabled="false"
                        style="margin-top: -6px;"
                        type="textarea"
                        autosize
                        v-model="textArea_user_id">
                    </el-input>
                  </el-col>
                </el-row>
              </div>

              <div class="demo-input-email" style="margin-top: 10px;">
                <el-row :gutter="2">
                  <el-col :span="12">
                    <div style="text-align: right">
                      职务 :
                    </div>
                  </el-col>
                  <el-col :span="12">
                    <el-input
                        :disabled="false"
                        style="margin-top: -6px;"
                        type="textarea"
                        autosize
                        v-model="textArea_user_groupID">
                    </el-input>
                  </el-col>
                </el-row>
              </div>
            </el-row>

            <el-row v-if="stop_pic_info_area" style="margin-top: 80px">

              <div class="demo-input-email" style="margin-top: 10px;">
                <el-row :gutter="2">
                  <el-col :span="12">
                    <div style="text-align: right">
                      检测到人数 :
                    </div>
                  </el-col>
                  <el-col :span="12">
                    <el-input
                        :disabled="false"
                        style="margin-top: -6px;"
                        type="textarea"
                        autosize
                        v-model="stop_textArea_user_num">
                    </el-input>
                  </el-col>
                </el-row>
              </div>

              <div class="demo-input-email" style="margin-top: 10px;">
                <el-row :gutter="2">
                  <el-col :span="12">
                    <div style="text-align: right">
                      姓名 :
                    </div>
                  </el-col>
                  <el-col :span="12">
                    <el-input
                        :disabled="false"
                        style="margin-top: -6px;"
                        type="textarea"
                        autosize
                        v-model="stop_textArea_user_name1">
                    </el-input>
                  </el-col>
                </el-row>
              </div>

              <div class="demo-input-email" style="margin-top: 10px;">
                <el-row :gutter="2">
                  <el-col :span="12">
                    <div style="text-align: right">
                      工号 :
                    </div>
                  </el-col>
                  <el-col :span="12">
                    <el-input
                        :disabled="false"
                        style="margin-top: -6px;"
                        type="textarea"
                        autosize
                        v-model="stop_textArea_user_id">
                    </el-input>
                  </el-col>
                </el-row>
              </div>

              <div class="demo-input-email" style="margin-top: 10px;">
                <el-row :gutter="2">
                  <el-col :span="12">
                    <div style="text-align: right">
                      职务 :
                    </div>
                  </el-col>
                  <el-col :span="12">
                    <el-input
                        :disabled="false"
                        style="margin-top: -6px;"
                        type="textarea"
                        autosize
                        v-model="stop_textArea_user_groupID">
                    </el-input>
                  </el-col>
                </el-row>
              </div>

            </el-row>

          </el-col>


          <!--          &lt;!&ndash;右边 2 &ndash;&gt;-->
          <!--          <el-col :span="4" class="grid">-->

          <!--            <el-row v-if="pic_info_area_2">-->
          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      姓名2 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="textArea_user_name2">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      工号2 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="textArea_user_id2">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      职务2 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="textArea_user_groupID2">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->
          <!--            </el-row>-->

          <!--            <el-row v-if="stop_pic_info_area_2">-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      姓名2 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="stop_textArea_user_name2">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      工号2 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="stop_textArea_user_id2">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      职务2 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="stop_textArea_user_groupID2">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->

          <!--            </el-row>-->

          <!--          </el-col>-->

          <!--          &lt;!&ndash;右边 3 &ndash;&gt;-->
          <!--          <el-col :span="4" class="grid">-->

          <!--            <el-row v-if="pic_info_area_3">-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      姓名3 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="textArea_user_name3">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      工号3 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="textArea_user_id3">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      职务3 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="textArea_user_groupID3">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->
          <!--            </el-row>-->

          <!--            <el-row v-if="stop_pic_info_area_3">-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      姓名3 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="stop_textArea_user_name3">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      工号3 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="stop_textArea_user_id3">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->

          <!--              <div class="demo-input-email" style="margin-top: 10px;">-->
          <!--                <el-row :gutter="2">-->
          <!--                  <el-col :span="12">-->
          <!--                    <div style="text-align: right">-->
          <!--                      职务3 :-->
          <!--                    </div>-->
          <!--                  </el-col>-->
          <!--                  <el-col :span="12">-->
          <!--                    <el-input-->
          <!--                        :disabled="false"-->
          <!--                        style="margin-top: -6px;"-->
          <!--                        type="textarea"-->
          <!--                        autosize-->
          <!--                        v-model="stop_textArea_user_groupID3">-->
          <!--                    </el-input>-->
          <!--                  </el-col>-->
          <!--                </el-row>-->
          <!--              </div>-->

          <!--            </el-row>-->

          <!--          </el-col>-->


        </div>
      </el-col>

      <el-col :span="1">
        <div class="grid-content-userInfo bg-purple-dark-userInfo"></div>
      </el-col>
    </el-row>

    <!-- 弹出sign up 界面-->
    <el-dialog title="上传用户" :visible.sync="signUpAble">
      <el-row>
        <el-form :model="formSignUp">
          <el-form-item label="ID/用户ID" :label-width="formLabelWidth">
            <el-input v-model="formSignUp.user_id" placeholder="not null/必填"
                      autocomplete="off"></el-input>
          </el-form-item>

          <el-form-item label="group ID:" :label-width="formLabelWidth">
            <el-input v-model="formSignUp.group_id" placeholder="not null/必填"
                      autocomplete="off"></el-input>
          </el-form-item>

          <el-form-item label="name/用户名:" :label-width="formLabelWidth">
            <el-input v-model="formSignUp.user_info" placeholder="not null/必填"
                      autocomplete="off"></el-input>
          </el-form-item>

          <el-form-item label="gender/性别:" :label-width="formLabelWidth">
            <el-select v-model="select" placeholder="请选择">
              <el-option label="男" value="男"></el-option>
              <el-option label="女" value="女"></el-option>
            </el-select>
          </el-form-item>


          <el-upload
              action=""
              multiple
              :limit="1"
              accept=".jpg,.jpeg,.png,.gif,.bmp,.pdf,.JPG,.JPEG,.PBG,.GIF,.BMP,.PDF"
              :on-change="handle_change"
              :on-remove="handle_remove"
              :on-exceed="handleExceed"
              :before-upload="uploadBefore"
              :auto-upload="false"
              :file-list="fileList"
              list-type="picture">
            <el-button slot="trigger" size="medium" type="primary"
                       style="float:left; font-size:16px; margin: 10px">点击这里上传图片
            </el-button>
            <el-button size="medium" type="primary"
                       style="float:left; font-size:16px; margin: 10px"
                       @click.prevent="takePhoto()">点击这里拍照
            </el-button>
            <div slot="tip" class="el-upload__tip">拍照和选图片上传2选1即可</div>
          </el-upload>

        </el-form>
      </el-row>
      <el-row>
        <el-button
            type="primary"
            style="float:left; font-size:16px; margin: 10px"
            @click.prevent="createNewResource()"> 点这里上传
        </el-button>
      </el-row>
    </el-dialog>


    <!-- 弹出 照相 界面-->
    <el-dialog title="拍照上传" :visible.sync="takePhotoAble" width="80%">

      <el-row>
        <!--开启摄像头-->
        <el-button type="primary" style="margin: 5px" @click.prevent="callCamera()">打开摄像头</el-button>
        <!--确认-->
        <el-button type="primary" style="margin: 5px" @click.prevent="photograph()">拍一张照</el-button>
        <el-button type="primary" style="margin: 5px" @click.prevent="uploadBycam()">点这里上传</el-button>
      </el-row>
      <el-row>
        <!--canvas截取流-->
        <canvas ref="canvas" width="500" height="375"></canvas>
        <!--图片展示-->
        <video ref="video" width="500" height="375" autoplay></video>
      </el-row>
    </el-dialog>


    <br>
  </div>
</template>
<style>
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
  created() {
    this.initUserInfo();
  },
  data() {
    return {
      headImgSrc: '',
      takePhotoAble: false,
      picByCam: '',

      // 搜索内嵌下拉框的value,这里给一个初始化的默认值1，也就是对应的male
      select: "男",

      fake_ret: {
        "result": 0,
        "message": "SUCCESS",
        "image": "123",
        "faces": [{
          "user_id": "10098440",
          "group_id": "staff",
          "user_info": "康佳慧",
          "box": [390, 167, 545, 322],
          "distance": 0.34566974479547136
        }]
      },

      textArea_specific_user: '',  //指定某个人


      textArea_user_num: '',
      textArea_user_name1: '',
      textArea_user_id: '',
      textArea_user_groupID: '',

      pic_info_area_s2: false,

      stop_textArea_user_num: '',
      stop_textArea_user_name1: '',
      stop_textArea_user_id: '',
      stop_textArea_user_groupID: '',

      textArea_user_name2: '',
      textArea_user_id2: '',
      textArea_user_groupID2: '',

      stop_textArea_user_name2: '',
      stop_textArea_user_id2: '',
      stop_textArea_user_groupID2: '',

      textArea_user_name3: '',
      textArea_user_id3: '',
      textArea_user_groupID3: '',

      stop_textArea_user_name3: '',
      stop_textArea_user_id3: '',
      stop_textArea_user_groupID3: '',

      pic_default: true,
      pic_area: false,
      pic_area_key: false,
      stop_pic_area: false,
      stop_pic_area_key: false,

      flow_img: '',  //图片
      flow_img_key: '',  //图片
      stop_flow_img: '',
      stop_flow_img_key: "",

      pic_show: true,

      stop_pic_done: false,

      pic_info_area: false,
      stop_pic_info_area: true,
      pic_info_area_2: true,
      stop_pic_info_area_2: true,
      pic_info_area_3: true,
      stop_pic_info_area_3: true,


      signUpAble: false,
      formLabelWidth: '220px',
      formSignUp: {
        group_id: '',
        user_info: '',
        user_id: '',
        user_image: ''
      },

      fileList: [],
      // upload 组件不支持自动更新 file list，所以设置 on-success 和 on-remove 的回调处理，将当前文件放到fileList2 副本中
      fileList2: [],


      test_model: false, //测试模式
      stop_detc_flag: false,   // 为真时，停止向服务器的请求
      // intervalID: '', // 定时任务ID
      websocket_linked: false,

      textArea_test: '123',
      count_t: 0,


      flow_img222222: "",


    };
  },
  methods: {


    // 调用摄像头
    callCamera() {
      // H5调用电脑摄像头API
      navigator.mediaDevices.getUserMedia({
        video: true
      }).then(success => {
        // 摄像头开启成功
        this.$refs['video'].srcObject = success
        // 实时拍照效果
        this.$refs['video'].play()
      }).catch(error => {
        console.error('摄像头开启失败，请检查摄像头是否可用！')
      })
    },
    // 拍照
    photograph() {
      this.picByCam = '';

      let ctx = this.$refs['canvas'].getContext('2d')
      // 把当前视频帧内容渲染到canvas上
      ctx.drawImage(this.$refs['video'], 0, 0, 500, 375)
      // 转base64格式、图片格式转换、图片质量压缩
      let imgBase64 = this.$refs['canvas'].toDataURL('image/jpeg', 0.7)

      // 由字节转换为KB 判断大小
      let str = imgBase64.replace('data:image/jpeg;base64,', '')
      let strLength = str.length
      let fileLength = parseInt(strLength - (strLength / 8) * 2)
      // 图片尺寸  用于判断
      let size = (fileLength / 1024).toFixed(2)
      console.log(size)

      // 上传拍照信息  调用接口上传图片 .........
      this.picByCam = str;
      // // 保存到本地
      // this.dialogCamera = false
      // let ADOM = document.createElement('a')
      // ADOM.href = this.headImgSrc
      // ADOM.download = new Date().getTime() + '.jpeg'
      // ADOM.click()
    },
    // 关闭摄像头
    closeCamera() {
      if (!this.$refs['video'].srcObject) {
        this.dialogCamera = false
        return
      }
      let stream = this.$refs['video'].srcObject
      let tracks = stream.getTracks()
      tracks.forEach(track => {
        track.stop()
      })
      this.$refs['video'].srcObject = null
    },

    //摄像头上传
    uploadBycam() {
      let _this = this;
      if (this.formSignUp.user_id == null || this.formSignUp.group_id == null || this.formSignUp.user_info == null) {
        this.$message('创建失败，group id, id ,name 不能为空！请输入信息');
        return;
      }
      if (this.picByCam == '') {
        this.$message('创建失败，请先打开摄像头，再点击拍一张图!');
        return;
      } else {
        this.$confirm('你确定要上传吗？', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '我再想想',
          type: 'info '
        }).then(() => {

          let formData = new FormData();
          formData.append("user_id", _this.formSignUp.user_id);
          formData.append("group_id", _this.formSignUp.group_id);
          formData.append("user_info", _this.formSignUp.user_info);
          formData.append("gender", _this.select);
          formData.append("user_image", _this.picByCam);
          _this.$upload.post("uploadInfo2", formData)
              .then(res => {
                _this.$message("成功, cheers !");
                _this.signUpAble = false;
                _this.takePhotoAble = false;
              }).catch(data => {
            _this.$message("failed!");
          })

        }).catch(() => {
        });
      }
    },

    //websocket 连接
    runSocket() {
      let count_rev = 0;
      this.ws = new WebSocket("ws://10.20.35.134:5678/");
      // this.ws = new WebSocket("ws://10.20.50.163:5678/");
      // this.ws = new WebSocket("ws://10.20.40.68:5678/");
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
      this.websocket_linked = true
    },
    // 定义 websocket onerror属性的函数
    websocketonerror: function (e) {
      console.log('WebSocket连接发生错误');
    },
    // 定义 websocket onmessage属性的函数
    websocketonmessage: function (e) {
      this.pic_default = false;
      this.pic_info_area_s2 = true;
      this.count_t = this.count_t + 1;
      let result = JSON.parse(e.data);
      if (result.message === 'SUCCESS') {
        if (!this.stop_pic_done) {
          this.flow_img = result.image;
          this.flow_img_key = result.image_key;
          this.textArea_user_num = result.faces.length;
          this.show_flow(this.textArea_user_num);
          // this.flow_img222222 = result.faces[0].image;
          if (this.textArea_user_num < 1) {
            this.textArea_user_name1 = '';
            this.textArea_user_id = '';
            this.textArea_user_groupID = '';
          } else if (this.textArea_user_num == 1) {
            this.textArea_user_name1 = result.faces[0].user_info;
            this.textArea_user_id = result.faces[0].user_id;
            this.textArea_user_groupID = result.faces[0].group_id;
          } else if (this.textArea_user_num == 2) {
            this.textArea_user_name1 = result.faces[0].user_info;
            this.textArea_user_id = result.faces[0].user_id;
            this.textArea_user_groupID = result.faces[0].group_id;
            this.textArea_user_name2 = result.faces[1].user_info;
            this.textArea_user_id2 = result.faces[1].user_id;
            this.textArea_user_groupID2 = result.faces[1].group_id;
          } else {
            this.textArea_user_name1 = result.faces[0].user_info;
            this.textArea_user_id = result.faces[0].user_id;
            this.textArea_user_groupID = result.faces[0].group_id;
            this.textArea_user_name2 = result.faces[1].user_info;
            this.textArea_user_id2 = result.faces[1].user_id;
            this.textArea_user_groupID2 = result.faces[1].group_id;
            this.textArea_user_name3 = result.faces[2].user_info;
            this.textArea_user_id3 = result.faces[2].user_id;
            this.textArea_user_groupID3 = result.faces[2].group_id;

          }
        }


      } else {
        // this.stop_detc_flag = true;
      }

    },
    // 定义 websocket onclose属性的函数
    websocketclose: function (e) {
      this.$message({
        message: '服务器连接关闭了...',
        type: 'success'
      });
      this.pic_default = true;
      this.pic_area = false;
      this.pic_area_key = false;
      this.stop_pic_area_key = false;
      this.stop_pic_area = false;
    },

    //启动websocket 连接
    openTest() {
      // window.location.reload();
      this.runSocket();

    },


    // 界面进来就会根据localStorage存储的当前用户信息，初始化用户详情
    initUserInfo() {

      // 隐藏上传界面
      this.signUpAble = false;
      this.takePhotoAble = false;
      this.stop_pic_done = false;

      // 展示流动框，关闭瞬时框
      this.show_flow(0);
      this.pic_default = true;
      this.pic_area = false;
      this.pic_area_key = false;
      this.stop_pic_area_key = false;
      this.stop_pic_area = false;

    },


    show_flow(num) {
      this.pic_area = true;
      this.pic_area_key = true;
      this.stop_pic_area_key = false;
      this.stop_pic_area = false;

      if (num == 0) {
        this.pic_info_area = false;
        this.stop_pic_info_area = false;
        this.pic_info_area_2 = false;
        this.stop_pic_info_area_2 = false;
        this.pic_info_area_3 = false;
        this.stop_pic_info_area_3 = false;
      } else if (num == 1) {
        this.pic_info_area = true;
        this.stop_pic_info_area = false;
        this.pic_info_area_2 = false;
        this.stop_pic_info_area_2 = false;
        this.pic_info_area_3 = false;
        this.stop_pic_info_area_3 = false;
      } else if (num == 2) {
        this.pic_info_area = true;
        this.stop_pic_info_area = false;
        this.pic_info_area_2 = true;
        this.stop_pic_info_area_2 = false;
        this.pic_info_area_3 = false;
        this.stop_pic_info_area_3 = false;
      } else {
        this.pic_info_area = true;
        this.stop_pic_info_area = false;
        this.pic_info_area_2 = true;
        this.stop_pic_info_area_2 = false;
        this.pic_info_area_3 = true;
        this.stop_pic_info_area_3 = false;
      }
    },

    show_non_flow(num) {

      this.pic_area = false;
      this.pic_area_key = false;
      this.stop_pic_area_key = true;
      this.stop_pic_area = true;

      if (num == 0) {
        this.pic_info_area = false;
        this.stop_pic_info_area = false;
        this.pic_info_area_2 = false;
        this.stop_pic_info_area_2 = false;
        this.pic_info_area_3 = false;
        this.stop_pic_info_area_3 = false;
      } else if (num == 1) {
        this.pic_info_area = false;
        this.stop_pic_info_area = true;
        this.pic_info_area_2 = false;
        this.stop_pic_info_area_2 = false;
        this.pic_info_area_3 = false;
        this.stop_pic_info_area_3 = false;
      } else if (num == 2) {
        this.pic_info_area = false;
        this.stop_pic_info_area = true;
        this.pic_info_area_2 = false;
        this.stop_pic_info_area_2 = true;
        this.pic_info_area_3 = false;
        this.stop_pic_info_area_3 = false;
      } else {
        this.pic_info_area = false;
        this.stop_pic_info_area = true;
        this.pic_info_area_2 = false;
        this.stop_pic_info_area_2 = true;
        this.pic_info_area_3 = false;
        this.stop_pic_info_area_3 = true;
      }
    },

    openSignUp() {
      this.signUpAble = true;
    },

    takePhoto() {
      if (this.formSignUp.user_id == null || this.formSignUp.group_id == null || this.formSignUp.user_info == null) {
        this.$message('group id, id ,name 不能为空！请先输入信息');
        return;
      }
      this.takePhotoAble = true;
    },

    handleExceed(files, fileList) {
      this.$message.warning(`当前限制最多上传 1 个文件`);
    },

    //https://element.eleme.cn/#/zh-CN/component/upload
    //fileList 存的是移除之后的文件，file是选择移除的那个文件，这个函数在  “移除文件时被调用”
    handle_remove(file, fileList) {
      this.fileList2 = fileList;
    },

    //这个函数在  上传文件时被调用
    handle_change(file, fileList) {
      this.fileList2 = fileList;
    },
    uploadBefore(file) {
      if (file.size > 1.5 * 10 * 1024 * 1024) {
        this.$message.error("File size exceeded 15M!");
        return false;
      }
    },

    createNewResource() {
      let _this = this;
      if (this.formSignUp.user_id == null || this.formSignUp.group_id == null || this.formSignUp.user_info == null) {
        this.$message('创建失败，group id, id ,name 不能为空！请输入信息');
        return;
      }
      if (!this.fileList2.length > 0) {
        this.$message('创建失败，图片不能为空！请上传图片');
        return;
      } else {
        this.$confirm('你确定要上传吗？', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '我再想想',
          type: 'info '
        }).then(() => {

          this.uploadImg(_this.fileList2);

        }).catch(() => {

          this.$message('发生了奇怪的bug,失败了,请联系管理员~~');

        });
      }
    },


    uploadImg(fileList2) {
      let _this = this;
      let formData = new FormData();
      formData.append("user_id", this.formSignUp.user_id);
      formData.append("group_id", this.formSignUp.group_id);
      formData.append("user_info", this.formSignUp.user_info);
      formData.append("gender", this.select);
      formData.append("user_image", fileList2[0].raw);
      _this.$upload.post("uploadInfo", formData)
          .then(res => {
            _this.$message("成功, cheers !");
          }).catch(data => {
        _this.$message("failed!");
      })
    },

    // 点击开始，会持续不断地请求后台服务，直至进程挂掉，或者进行界面刷新
    start_detc() {
      if (!this.websocket_linked) {
        this.$message({
          message: '正在和服务器建立连接...',
          type: 'success'
        });
      }
      this.stop_pic_done = false;
      this.openTest();
      //旧的轮询逻辑
      // this.show_flow();
      // this.intervalID = setInterval(function () {
      //   _this.start_detc_1();
      // }, 800);
    },

    stop_detc() {
      this.stop_pic_done = true;

      this.stop_flow_img = this.flow_img;
      this.stop_flow_img_key = this.flow_img_key;
      this.stop_textArea_user_num = this.textArea_user_num;

      this.show_non_flow(this.textArea_user_num);
      if (this.textArea_user_num < 1) {
        this.stop_textArea_user_name1 = '';
        this.stop_textArea_user_id = '';
        this.stop_textArea_user_groupID = '';
      } else if (this.textArea_user_num == 1) {
        this.stop_textArea_user_name1 = this.textArea_user_name1;
        this.stop_textArea_user_id = this.textArea_user_id;
        this.stop_textArea_user_groupID = this.textArea_user_groupID;
      } else if (this.textArea_user_num == 2) {
        this.stop_textArea_user_name1 = this.textArea_user_name1;
        this.stop_textArea_user_id = this.textArea_user_id;
        this.stop_textArea_user_groupID = this.textArea_user_groupID;
        this.stop_textArea_user_name2 = this.textArea_user_name2;
        this.stop_textArea_user_id2 = this.textArea_user_id2;
        this.stop_textArea_user_groupID2 = this.textArea_user_groupID2;
      } else {
        this.stop_textArea_user_name1 = this.textArea_user_name1;
        this.stop_textArea_user_id = this.textArea_user_id;
        this.stop_textArea_user_groupID = this.textArea_user_groupID;
        this.stop_textArea_user_name2 = this.textArea_user_name2;
        this.stop_textArea_user_id2 = this.textArea_user_id2;
        this.stop_textArea_user_groupID2 = this.textArea_user_groupID2;
        this.stop_textArea_user_name3 = this.textArea_user_name3;
        this.stop_textArea_user_id3 = this.textArea_user_id3;
        this.stop_textArea_user_groupID3 = this.textArea_user_groupID3;

      }
      // // clearInterval(this.intervalID); // 清除定时器
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