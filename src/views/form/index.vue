<template>
  <div class="app-container">
      <el-form ref="form" :model="form" label-width="80px">
  <el-form-item label="标题">
    <el-input v-model="form.name"></el-input>
  </el-form-item>
  <el-form-item label="图片">
    <el-input v-model="form.url"></el-input>
  </el-form-item>
  <el-form-item label="价格">
    <el-input v-model="form.oldprice"></el-input>
  </el-form-item>
  <el-form-item label="分类">
    <el-select v-model="form.region" placeholder="请选择活动区域">
      <el-option label="javascript" value="shanghai"></el-option>
      <el-option label="nodejs" value="beijing"></el-option>
    </el-select>
  </el-form-item>
  <el-form-item label="活动时间">
    <el-col :span="11">
      <el-date-picker type="date" placeholder="选择日期" v-model="form.date1" style="width: 100%;"></el-date-picker>
    </el-col>
    <el-col class="line" :span="2">-</el-col>
    <el-col :span="11">
      <el-time-picker type="fixed-time" placeholder="选择时间" v-model="form.date2" style="width: 100%;"></el-time-picker>
    </el-col>
  </el-form-item>
  <el-form-item label="优惠劵">
    <el-switch v-model="form.delivery"></el-switch>
  </el-form-item>
  <el-form-item label="劵">
    <el-select v-model="form.region" placeholder="请选择活动区域">
      <el-option label="3" value="shanghai"></el-option>
      <el-option label="4" value="beijing"></el-option>
    </el-select>
  </el-form-item>
  <el-form-item label="新价格">
    <el-input v-model="form.newprice"></el-input>
  </el-form-item>
 
  <el-form-item label="口令">
    <el-input v-model="form.newprice"></el-input>
  </el-form-item>
 
 
  <el-form-item>
    <el-button type="primary" @click="onSubmit">立即创建</el-button>
    <el-button>取消</el-button>
  </el-form-item>
</el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      }
    }
  },
  methods: {
    onSubmit() {
      this.$message('submit!')
    },
    onCancel() {
      this.$message({
        message: 'cancel!',
        type: 'warning'
      })
    }
  }
}
</script>

<style scoped>
.line{
  text-align: center;
}
</style>

