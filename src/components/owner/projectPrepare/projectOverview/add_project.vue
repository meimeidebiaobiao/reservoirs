<template>
  <el-form ref="form"
           :model="form"
           label-width="160px"
           class="project-form"
           :rules="rules"
           id="addProject">
    <!-- <div class="project-depart">
            <span>项目所属：</span>
            <el-radio-group v-model="form.affiliatedTo">
                <el-radio-button label="govern">水利厅直管</el-radio-button>
                <el-radio-button label="corp">水投直管</el-radio-button>
            </el-radio-group>
        </div> -->
    <el-card class="box-card">
      <div slot="header"
           class="clearfix">
        <span class="project-panel-title"><i class="fa fa-info-circle"></i> 基础信息</span>
      </div>
      <el-row :gutter="20">
        <!-- <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="项目所属">
            <el-radio-group v-model="form.affiliatedTo"
                            size="medium"
                            prop="affiliatedTo">
              <el-radio-button label="govern">水利厅直管</el-radio-button>
              <el-radio-button label="corp">水投直管</el-radio-button>
            </el-radio-group>
          </el-form-item>
        </el-col> -->
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="项目名称"
                        prop="plantName">
            <el-input v-model="form.plantName"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="12"
                :md="12"
                :xs="12">
          <el-form-item label="项目法人"
                        prop="legalPersonName">
            <el-input v-model="form.legalPersonName"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="12"
                :md="12"
                :xs="12">
          <el-form-item label="法人代表"
                        prop="legalRepresentativeName">
            <el-input v-model="form.legalRepresentativeName"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="12"
                :md="12"
                :xs="12">
          <el-form-item label="所在县">
            <!-- <el-input v-model="form.county"></el-input> -->
            <el-cascader :options="options"
                         :show-all-levels="false"
                         ref="regionSelector"
                         @change="selectedRegion"></el-cascader>
          </el-form-item>
        </el-col>
        <el-col :lg="12"
                :md="12"
                :xs="12">
          <el-form-item label="所在地"
                        prop="location">
            <el-input v-model="form.location"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="12"
                :md="12"
                :xs="12">
          <el-form-item label="经度"
                        prop="longitude">
            <el-input v-model="form.longitude"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="12"
                :md="12"
                :xs="12">
          <el-form-item label="纬度"
                        prop="latitude">
            <el-input v-model="form.latitude"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
    </el-card>
    <el-card class="box-card">
      <div slot="header"
           class="clearfix">
        <span class="project-panel-title"><i class="fa fa-book"></i> 水库资料</span>
      </div>
      <el-row :gutter="20">
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="项目类型"
                        prop="projectType">
            <el-input v-model="form.projectType"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="工程级别"
                        prop="level">
            <el-input v-model="form.level"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="规模"
                        prop="scale">
            <el-input v-model="form.scale"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="坝型"
                        prop="damType">
            <el-input v-model="form.damType"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="最大坝高（m）"
                        prop="maxDamHeight">
            <el-input v-model="form.maxDamHeight"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="溢洪道（m）"
                        prop="spillway">
            <el-input v-model="form.spillway"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="灌溉面积(万亩）"
                        prop="irrigatedArea">
            <el-input v-model="form.irrigatedArea"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="积水面积（m）"
                        prop="catchmentArea">
            <el-input v-model="form.catchmentArea"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="度汛高程"
                        prop="floodControlElevation">
            <el-input v-model="form.floodControlElevation"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="总库容"
                        prop="storage">
            <el-input v-model="form.storage"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="兴利库容"
                        prop="utilizablCapacity">
            <el-input v-model="form.utilizablCapacity"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="装机容积（Kw）"
                        prop="installedCapacity">
            <el-input v-model="form.installedCapacity"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="12"
                :md="12"
                :xs="12">
          <el-form-item label="城镇供水人口（万人)"
                        prop="waterSupplyPopulation">
            <el-input v-model="form.waterSupplyPopulation"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="12"
                :md="12"
                :xs="12">
          <el-form-item label="农村人饮（万人）"
                        prop="ruralHumanWater">
            <el-input v-model="form.ruralHumanWater"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="12"
                :md="12"
                :xs="12">
          <el-form-item label="大牲畜（万头）"
                        prop="livestock">
            <el-input v-model="form.livestock"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="12"
                :md="12"
                :xs="12">
          <el-form-item label="供水量（万m³/年)"
                        prop="watersupply">
            <el-input v-model="form.watersupply"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
    </el-card>
    <el-card class="box-card">
      <div slot="header"
           class="clearfix">
        <span class="project-panel-title"><i class="fa fa-bank"></i> 工程信息</span>
      </div>
      <el-row :gutter="20">
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="项目来源"
                        prop="projectSource">
            <el-input v-model="form.projectSource"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="工期（月）"
                        prop="timeLimit">
            <el-input v-model="form.timeLimit"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="总投资"
                        prop="totalInvestment">
            <el-input v-model="form.totalInvestment"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="工程占地（亩）"
                        prop="areaCoverage">
            <el-input v-model="form.areaCoverage"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="">
            <!-- <el-input v-model="form.hasSignedConstructionContract"></el-input> -->
            <el-checkbox v-model="form.hasSignedConstructionContract">是否签订枢纽工程施工承包合同</el-checkbox>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="">
            <!-- <el-input v-model="form.hasAcceptCompletion"></el-input> -->
            <el-checkbox v-model="form.hasAcceptCompletion">枢纽工程是否完工</el-checkbox>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="12"
                :xs="12">
          <el-form-item label="">
            <!-- <el-input v-model="form.hasProjectCompleted"></el-input> -->
            <el-checkbox v-model="form.hasProjectCompleted">是否竣工验收</el-checkbox>
          </el-form-item>
        </el-col>
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="监理、施工招标情况">
            <el-input v-model="form.supervisorBid"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="8"
                :xs="12">
          <el-form-item label="单位工程数"
                        prop="unitProjectAmount">
            <el-input v-model="form.unitProjectAmount"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="8"
                :xs="12">
          <el-form-item label="单元工程数"
                        prop="cellProjectAmount">
            <el-input v-model="form.cellProjectAmount"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="8"
                :md="8"
                :xs="12">
          <el-form-item label="分布工程数"
                        prop="branchProjectAmount">
            <el-input v-model="form.branchProjectAmount"></el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="项目概况"
                        prop="overview">
            <el-input type="textarea"
                      :rows="5"
                      placeholder="请输入内容"
                      v-model="form.overview">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="工程任务及主要建筑物">
            <el-input type="textarea"
                      :rows="5"
                      placeholder="请输入内容"
                      v-model="form.projectTask">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="建设用地">
            <el-input type="textarea"
                      :rows="5"
                      placeholder="请输入内容"
                      v-model="form.constructionLand">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="土地复垦方案">
            <el-input type="textarea"
                      :rows="5"
                      placeholder="请输入内容"
                      v-model="form.landReclamationPlan">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="单位工程概况">
            <el-input type="textarea"
                      :rows="5"
                      placeholder="请输入内容"
                      v-model="form.unitProjectOverview">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="单元工程概况">
            <el-input type="textarea"
                      :rows="5"
                      placeholder="请输入内容"
                      v-model="form.cellProjectOverview">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="分布工程概况">
            <el-input type="textarea"
                      :rows="5"
                      placeholder="请输入内容"
                      v-model="form.branchProjectOverview">
            </el-input>
          </el-form-item>
        </el-col>
        <el-col :lg="24"
                :md="24"
                :xs="24">
          <el-form-item label="备注">
            <el-input type="textarea"
                      :rows="5"
                      placeholder="请输入内容"
                      v-model="form.remark">
            </el-input>
          </el-form-item>
        </el-col>
      </el-row>
    </el-card>
    <el-card class="box-card">
      <div slot="header"
           class="clearfix">
        <span>附件</span>
      </div>
      <el-upload class="upload-demo"
                 list-type="picture-card"
                 action=""
                 ref="fileUpload"
                 multiple
                 :auto-upload="false"
                 :file-list="fileList">
        <!-- <el-button size="small" type="primary">点击上传</el-button> -->
        <i class="el-icon-plus"></i>
      </el-upload>
    </el-card>
    <div class="tool-bar">
      <el-button type="primary"
                 @click="detailSubmit">提交</el-button>
    </div>
  </el-form>
</template>

<script>
export default {
  data() {
    return {
      form: {
        affiliatedTo: 'govern',
        hasSignedConstructionContract: false,
        hasAcceptCompletion: false,
        hasProjectCompleted: false
      },
      fileList: [],
      options: [],
      rules: {
        affiliatedTo: [
          { required: true, message: '必填', trigger: 'blur' }
        ],
        plantName: [
          { required: true, message: '必填', trigger: 'blur' }
        ],
        legalPersonName: [
          { required: true, message: '必填', trigger: 'blur' }
        ],
        legalRepresentativeName: [
          { required: true, message: '必填', trigger: 'blur' }
        ],
        location: [
          { required: true, message: '必填', trigger: 'blur' }
        ],
        longitude: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        latitude: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        projectType: [
          { required: true, message: '必填', trigger: 'blur' }
        ],
        level: [
          { required: true, message: '必填', trigger: 'blur' }
        ],
        scale: [
          { required: true, message: '必填', trigger: 'blur' }
        ],
        damType: [
          { required: true, message: '必填', trigger: 'blur' }
        ],
        maxDamHeight: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        spillway: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        irrigatedArea: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        catchmentArea: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        floodControlElevation: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        storage: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        utilizablCapacity: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        installedCapacity: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        waterSupplyPopulation: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        ruralHumanWater: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        livestock: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        watersupply: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        projectSource: [
          { required: true, message: '必填', trigger: 'blur' }
        ],
        timeLimit: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        totalInvestment: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        areaCoverage: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        unitProjectAmount: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        cellProjectAmount: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        branchProjectAmount: [
          { required: true, validator: this.validNum, trigger: 'blur' }
        ],
        overview: [
          { required: true, message: '必填', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    validNum(rule, value, callback) {
      if (!value) {
        return callback(new Error('必填'))
      } else if (isNaN(value)) {
        return callback(new Error('只能填数字！'))
      } else {
        callback()
      }
    },
    detailSubmit() {
      this.$refs['form'].validate((valid) => {
        if (valid) {
          let files = this.$refs.fileUpload.uploadFiles
          this.$common.uploadFile(files).then(id => {
            id && (this.form.tempFolderRelativePath = id)
            this.$http.post('/api/pre/registerProject', this.form, { loading: { operation: true } }).then(result => {
              if (result.code === 1002) {
                this.$message({ type: 'success', message: '创建成功！' })
                this.getMyBaseInfo()
                this.$router.push({ path: '/projectprepare/projectoverview' })
                this.$store.dispatch('setIsRegister', true)
              } else {
                this.$alert(result.data, '错误', { type: 'warning' })
              }
            }, resultErr => {
              this.$alert('创建失败！', '错误', { type: 'warning' })
            })
          })
        }
      })
    },
    getMyBaseInfo() {
      let Base64 = require('js-base64').Base64
      this.$http.get('/api/baseinfo/mybaseinfo', { loading: { target: '#addProject' } }).then(res => {
        if (res.code === 1002) {
          let reservoir = res.data
          this.reservoir = reservoir
          window.localStorage.RESERVOIR = Base64.encode(JSON.stringify(reservoir))
        } else {
          window.localStorage.RESERVOIR = ''
        }
      })
    },
    getAllRegion() {
      this.$http.get('/api/region/all', { loading: { target: '#addProject' } }).then(res => {
        let data = res.data
        if (data && data.length > 0) {
          data.map(item => {
            item.label = item.regionName
            item.value = item.regionId
            return item
          })
        }
        let treeData = this.$store.state.buildTree(data, 'regionId', 'parentId')
        this.options = treeData
      })
    },
    selectedRegion(value) {
      let widget = this.$refs.regionSelector
      this.form.regionId = value[value.length - 1]
      this.form.county = widget.currentLabels[value.length - 1]
    }
  },
  mounted() {
    this.getAllRegion()
  }
}
</script>

<style>
.project-panel-title {
  font-size: 16px;
}
.project-panel-title > i {
  font-size: 18px;
}
</style>
