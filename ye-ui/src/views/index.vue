<template>
  <div class="app-container home">
    <el-row :gutter="20">
      <el-col :sm="24" :lg="24">
        <blockquote class="text-warning" style="font-size: 14px">
          占位001
        </blockquote>

        <hr />
      </el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :sm="24" :lg="12" style="padding-left: 20px">
        <h2>南昌生活站</h2>
        <p>
          O2O平台，提供超市购物、快递代收、在线租房、家政服务等一系列服务
        </p>
        <p>
          <b>当前版本:</b> <span>v{{ version }}</span>
        </p>
        <p>
          <el-tag type="danger">&yen;免费开源</el-tag>
        </p>
        <p>
          <el-button
            type="primary"
            size="mini"
            icon="el-icon-cloudy"
            plain
            @click="goTarget('https://gitee.com/y_project/ye-Vue')"
            >访问码云</el-button
          >
          <el-button
            size="mini"
            icon="el-icon-s-home"
            plain
            @click="goTarget('http://ye.vip')"
            >访问主页</el-button
          >
        </p>
      </el-col>

      <el-col :sm="24" :lg="12" style="padding-left: 50px">
        <el-row>
          <el-col :span="12">
            <h2>技术选型</h2>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="6">
            <h4>后端技术</h4>
            <ul>
              <li>SpringBoot</li>
              <li>Spring Security</li>
              <li>JWT</li>
              <li>MyBatis</li>
              <li>Druid</li>
              <li>Fastjson</li>
              <li>...</li>
            </ul>
          </el-col>
          <el-col :span="6">
            <h4>前端技术</h4>
            <ul>
              <li>Vue</li>
              <li>Vuex</li>
              <li>Element-ui</li>
              <li>Axios</li>
              <li>Sass</li>
              <li>Quill</li>
              <li>...</li>
            </ul>
          </el-col>
        </el-row>
      </el-col>
    </el-row>
    <el-divider />
    <el-row :gutter="20">
      <el-col :xs="24" :sm="24" :md="12" :lg="8">
        <el-card class="update-log">
          <div slot="header" class="clearfix">
            <span>联系信息</span>
          </div>
          <div class="body">
            <p>
              <i class="el-icon-s-promotion"></i> 官网：<el-link
                href="http://www.ye.vip"
                target="_blank"
                >http://www.ye.vip</el-link
              >
            </p>
            <p>
              <i class="el-icon-user-solid"></i> QQ群：<s> 满101046199 </s> <a href="https://jq.qq.com/?_wv=1027&k=tKEt51dz" target="_blank">136919097</a>
            </p>
            <p>
              <i class="el-icon-chat-dot-round"></i> 微信：<a
                href="javascript:;"
                >/ *王也</a
              >
            </p>
            <p>
              <i class="el-icon-money"></i> 支付宝：<a
                href="javascript:;"
                class="支付宝信息"
                >/ *王也</a
              >
            </p>
          </div>
        </el-card>
      </el-col>
      <el-col :xs="24" :sm="24" :md="12" :lg="8">
        <el-card class="update-log">
          <div slot="header" class="clearfix">
            <span>更新日志</span>
          </div>
          <el-collapse accordion>
            <el-collapse-item title="v0.0.1 - 2023-05-12">
              <ol>
                <li>定时任务违规的字符</li>
                <li>重置时取消部门选中</li>
                <li>新增返回警告消息提示</li>
                <li>忽略不必要的属性数据返回</li>
                <li>修改参数键名时移除前缓存配置</li>
                <li>导入更新用户数据前校验数据权限</li>
                <li>兼容Excel下拉框内容过多无法显示的问题</li>
                <li>升级echarts到最新版本5.4.0</li>
                <li>升级core-js到最新版本3.25.3</li>
                <li>升级oshi到最新版本6.4.0</li>
                <li>升级kaptcha到最新版2.3.3</li>
                <li>升级druid到最新版本1.2.15</li>
                <li>升级fastjson到最新版2.0.20</li>
                <li>升级pagehelper到最新版1.4.6</li>
                <li>优化弹窗内容过多展示不全问题</li>
                <li>优化swagger-ui静态资源使用缓存</li>
                <li>开启TopNav没有子菜单隐藏侧边栏</li>
                <li>删除fuse无效选项maxPatternLength</li>
                <li>优化导出对象的子列表为空会出现[]问题</li>
                <li>优化编辑头像时透明部分会变成黑色问题</li>
                <li>优化小屏幕上修改头像界面布局错位的问题</li>
                <li>修复代码生成勾选属性无效问题</li>
                <li>修复文件上传组件格式验证问题</li>
                <li>修复回显数据字典数组异常问题</li>
                <li>修复sheet超出最大行数异常问题</li>
                <li>修复Log注解GET请求记录不到参数问题</li>
                <li>修复调度日志点击多次数据不变化的问题</li>
                <li>修复主题颜色在Drawer组件不会加载问题</li>
                <li>修复文件名包含特殊字符的文件无法下载问题</li>
                <li>修复table中更多按钮切换主题色未生效修复问题</li>
                <li>修复某些特性的环境生成代码变乱码TXT文件问题</li>
                <li>修复代码生成图片/文件/单选时选择必填无法校验问题</li>
                <li>修复某些特性的情况用户编辑对话框中角色和部门无法修改问题</li>
                <li>其他细节优化</li>
              </ol>
            </el-collapse-item>
          </el-collapse>
        </el-card>
      </el-col>
      <el-col :xs="24" :sm="24" :md="12" :lg="8">
        <el-card class="update-log">
          <div slot="header" class="clearfix">
            <span>捐赠支持</span>
          </div>
          <div class="body">
            <!-- <img
              src="https://oscimg.oschina.net/oscnet/up-d6695f82666e5018f715c41cb7ee60d3b73.png"
              alt="donate"
              width="100%"
            /> -->
            <span style="display: inline-block; height: 30px; line-height: 30px"
              >你可以请作者喝杯咖啡表示鼓励</span
            >
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "Index",
  data() {
    return {
      // 版本号
      version: "3.8.5"
    };
  },
  methods: {
    goTarget(href) {
      window.open(href, "_blank");
    }
  }
};
</script>

<style scoped lang="scss">
.home {
  blockquote {
    padding: 10px 20px;
    margin: 0 0 20px;
    font-size: 17.5px;
    border-left: 5px solid #eee;
  }
  hr {
    margin-top: 20px;
    margin-bottom: 20px;
    border: 0;
    border-top: 1px solid #eee;
  }
  .col-item {
    margin-bottom: 20px;
  }

  ul {
    padding: 0;
    margin: 0;
  }

  font-family: "open sans", "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  color: #676a6c;
  overflow-x: hidden;

  ul {
    list-style-type: none;
  }

  h4 {
    margin-top: 0px;
  }

  h2 {
    margin-top: 10px;
    font-size: 26px;
    font-weight: 100;
  }

  p {
    margin-top: 10px;

    b {
      font-weight: 700;
    }
  }

  .update-log {
    ol {
      display: block;
      list-style-type: decimal;
      margin-block-start: 1em;
      margin-block-end: 1em;
      margin-inline-start: 0;
      margin-inline-end: 0;
      padding-inline-start: 40px;
    }
  }
}
</style>

