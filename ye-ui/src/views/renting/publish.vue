<template>
  <div>
    <el-row :gutter="22">
      <el-form ref="elForm" :model="formData" :rules="rules" size="medium" label-width="96px">
        <el-col :span="12">
          <el-form-item label="房屋位置" prop="location">
            <el-cascader v-model="formData.location" :options="locationOptions" :props="locationProps"
              :style="{width: '100%'}" placeholder="请选择房屋位置" filterable clearable></el-cascader>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="小区名称" prop="communityName">
            <el-input v-model="formData.communityName" placeholder="请输入小区名称" :maxlength="100" show-word-limit
              clearable prefix-icon='el-icon-location' :style="{width: '100%'}"></el-input>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="面积" prop="area">
            <el-input v-model="formData.area" placeholder="请输入面积" clearable :style="{width: '100%'}">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="朝向" prop="orientation">
            <el-radio-group v-model="formData.orientation" size="medium">
              <el-radio v-for="(item, index) in orientationOptions" :key="index" :label="item.value"
                :disabled="item.disabled">{{item.label}}</el-radio>
            </el-radio-group>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="所在楼层" prop="floor">
            <el-input v-model="formData.floor" placeholder="请输入所在楼层" clearable :style="{width: '100%'}">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="总楼层" prop="total_floor">
            <el-input v-model="formData.total_floor" placeholder="请输入总楼层" clearable :style="{width: '100%'}">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="房间数量" prop="rooms">
            <el-select v-model="formData.rooms" placeholder="请选择房间数量" clearable :style="{width: '100%'}">
              <el-option v-for="(item, index) in roomsOptions" :key="index" :label="item.label"
                :value="item.value" :disabled="item.disabled"></el-option>
            </el-select>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="客厅数量" prop="living_rooms">
            <el-select v-model="formData.living_rooms" placeholder="请选择客厅数量" clearable
              :style="{width: '100%'}">
              <el-option v-for="(item, index) in living_roomsOptions" :key="index" :label="item.label"
                :value="item.value" :disabled="item.disabled"></el-option>
            </el-select>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="水电类型" prop="electricity_type">
            <el-select v-model="formData.electricity_type" placeholder="请选择水电类型" filterable clearable
              :style="{width: '100%'}">
              <el-option v-for="(item, index) in electricity_typeOptions" :key="index" :label="item.label"
                :value="item.value" :disabled="item.disabled"></el-option>
            </el-select>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="设施" prop="facilities">
            <el-select v-model="formData.facilities" placeholder="请选择设施" multiple clearable
              :style="{width: '100%'}">
              <el-option v-for="(item, index) in facilitiesOptions" :key="index" :label="item.label"
                :value="item.value" :disabled="item.disabled"></el-option>
            </el-select>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="月租金" prop="monthly_rent">
            <el-input v-model="formData.monthly_rent" placeholder="请输入月租金" clearable :style="{width: '100%'}">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="押金" prop="deposit">
            <el-input v-model="formData.deposit" placeholder="请输入押金" clearable :style="{width: '100%'}">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="主图" prop="cover" required>
            <el-upload ref="cover" :file-list="coverfileList" :action="coverAction"
              :before-upload="coverBeforeUpload" list-type="picture-card">
              <i class="el-icon-plus"></i>
              <div slot="tip" class="el-upload__tip">只能上传不超过 2MB 的文件</div>
            </el-upload>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="房源照片" prop="photos" required>
            <el-upload ref="photos" :file-list="photosfileList" :action="photosAction" multiple
              :before-upload="photosBeforeUpload" list-type="picture-card" accept="image/*">
              <i class="el-icon-plus"></i>
              <div slot="tip" class="el-upload__tip">只能上传不超过 2MB 的image/*文件</div>
            </el-upload>
          </el-form-item>
        </el-col>
        <el-col :span="24">
          <el-form-item size="large">
            <el-button type="primary" @click="submitForm">提交</el-button>
            <el-button @click="resetForm">重置</el-button>
          </el-form-item>
        </el-col>
      </el-form>
    </el-row>
  </div>
</template>
<script>
export default {
  components: {},
  props: [],
  data() {
    return {
      formData: {
        location: [1, 2],
        communityName: '',
        area: '',
        orientation: '',
        floor: '',
        total_floor: '',
        rooms: '',
        living_rooms: '',
        electricity_type: 1,
        facilities: [],
        monthly_rent: '',
        deposit: '',
        cover: null,
        photos: [],
      },
      rules: {
        location: [{
          required: true,
          type: 'array',
          message: '请至少选择一个location',
          trigger: 'change'
        }],
        communityName: [{
          required: true,
          message: '请输入小区名称',
          trigger: 'blur'
        }],
        area: [{
          required: true,
          message: '请输入面积',
          trigger: 'blur'
        }],
        orientation: [{
          required: true,
          message: '朝向不能为空',
          trigger: 'change'
        }],
        floor: [{
          required: true,
          message: '请输入所在楼层',
          trigger: 'blur'
        }],
        total_floor: [{
          required: true,
          message: '请输入总楼层',
          trigger: 'blur'
        }],
        rooms: [{
          required: true,
          message: '请选择房间数量',
          trigger: 'change'
        }],
        living_rooms: [{
          required: true,
          message: '请选择客厅数量',
          trigger: 'change'
        }],
        electricity_type: [{
          required: true,
          message: '请选择水电类型',
          trigger: 'change'
        }],
        facilities: [{
          required: true,
          type: 'array',
          message: '请至少选择一个facilities',
          trigger: 'change'
        }],
        monthly_rent: [{
          required: true,
          message: '请输入月租金',
          trigger: 'blur'
        }],
        deposit: [{
          required: true,
          message: '请输入押金',
          trigger: 'blur'
        }],
      },
      coverAction: 'https://jsonplaceholder.typicode.com/posts/',
      coverfileList: [],
      photosAction: 'https://jsonplaceholder.typicode.com/posts/',
      photosfileList: [],
      locationOptions: [],
      orientationOptions: [{
        "label": "东",
        "value": 1
      }, {
        "label": "南",
        "value": 2
      }, {
        "label": "西",
        "value": 3
      }, {
        "label": "北",
        "value": 4
      }],
      roomsOptions: [{
        "label": "1房",
        "value": 1
      }, {
        "label": "2房",
        "value": 2
      }, {
        "label": "3房",
        "value": 3
      }, {
        "label": "4房",
        "value": 4
      }],
      living_roomsOptions: [{
        "label": "1房",
        "value": 1
      }, {
        "label": "2房",
        "value": 2
      }, {
        "label": "3房",
        "value": 3
      }, {
        "label": "4房",
        "value": 4
      }],
      electricity_typeOptions: [{
        "label": "民用",
        "value": 1
      }, {
        "label": "商用",
        "value": 2
      }],
      facilitiesOptions: [{
        "label": "是否有洗衣机",
        "value": 1
      }, {
        "label": "是否有空调",
        "value": 2
      }, {
        "label": "是否有衣柜",
        "value": 3
      }, {
        "label": "是否有电视",
        "value": 4
      }, {
        "label": "是否有电梯",
        "value": 5
      }, {
        "label": "是否有卫生间",
        "value": 6
      }, {
        "label": "是否有厨房",
        "value": 7
      }, {
        "label": "是否有阳台",
        "value": 8
      }, {
        "label": "是否有冰箱",
        "value": 9
      }, {
        "label": "是否有热水器",
        "value": 10
      }, {
        "label": "是否有天然气",
        "value": 11
      }, {
        "label": "是否有宽带",
        "value": 12
      }],
      locationProps: {
        "multiple": false
      },
    }
  },
  computed: {},
  watch: {},
  created() {},
  mounted() {},
  methods: {
    submitForm() {
      this.$refs['elForm'].validate(valid => {
        if (!valid) return
        // TODO 提交表单
      })
    },
    resetForm() {
      this.$refs['elForm'].resetFields()
    },
    getLocationOptions() {
      // TODO 发起请求获取数据
      this.locationOptions
    },
    coverBeforeUpload(file) {
      let isRightSize = file.size / 1024 / 1024 < 2
      if (!isRightSize) {
        this.$message.error('文件大小超过 2MB')
      }
      return isRightSize
    },
    photosBeforeUpload(file) {
      let isRightSize = file.size / 1024 / 1024 < 2
      if (!isRightSize) {
        this.$message.error('文件大小超过 2MB')
      }
      let isAccept = new RegExp('image/*').test(file.type)
      if (!isAccept) {
        this.$message.error('应该选择image/*类型的文件')
      }
      return isRightSize && isAccept
    },
  }
}

</script>
<style>
.el-upload__tip {
  line-height: 1.2;
}

</style>
