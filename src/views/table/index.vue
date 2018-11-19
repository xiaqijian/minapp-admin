<template>
  <div class="actbox-box">
    <div class="act-box">
      <div>
        <el-form :inline="true" :model="formInline" class="demo-form-inline">
          <el-form-item label="分类">
            <el-select v-model="formInline.sort" placeholder="分类">
              <el-option label="javascript" value="javascript"></el-option>
              <el-option label="node" value="node"></el-option>
              <el-option label="css" value="css"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="onSubmit">查询</el-button>
          </el-form-item>
        </el-form>
      </div>
      <el-row>
        <el-button>默认按钮</el-button>
        <el-button type="primary">搜索</el-button>
        <el-button type="danger">删除</el-button>
      </el-row>

    </div>
     <el-table
    :data="tableData"
    border
    :row-class-name="tableRowClassName"
    style="width: 100%">
     <el-table-column
      type="selection"
      width="55">
    </el-table-column>
    <el-table-column
      label="id"
      width="140"
      >
      <template slot-scope="scope">
        {{scope.row.id}}
      </template>
    </el-table-column>
    <el-table-column
      prop="name"
      label="标题"
      >
    </el-table-column>
    <el-table-column
      prop="jendtime"
      label="到期时间"
      width="180">
    </el-table-column>
    <el-table-column
      prop="tag"
      label="标签"
      width="100"
      >
      <template slot-scope="scope">
        <el-tag>{{scope.row.bDate === false ? '正常' : '过期'}}</el-tag>
      </template>
    </el-table-column>
     
  </el-table>
  </div>
  
</template>

<style>
.act-box {
  margin: 20px 0;
}
.actbox-box {
  padding: 20px;
}
.el-table .warning-row {
    background: #F56C6C;
    color: #fff;
  }

  .el-table .success-row {
    background: #f0f9eb;
  }
</style>


<script>
  export default {
    data() {
      return {
        tableData: [{
          jendtime: '2016-05-02',
          name: '王小虎',
          checked: true
        }],
        formInline: {
          sort: ''
        }
 
      }
    },
    mounted () {
      this.getData()
    },
    methods: {
      getData (sort ="javascript") {
           let that = this
          that.axios.get('/taobao/index?sort='+sort)
          .then((res)=> {
            console.log(res.data.data)
            that.tableData = res.data.data
          })
          .catch((err) => {
            console.log(err)
          })
      },
      tableRowClassName({row}) {
        console.log(row)
        console.log(row.bDate)
        let bDate = row.bDate
        if (bDate) {
          return 'warning-row';
        }
      },
      onSubmit () {
        let sort = this.formInline.sort
        this.getData(sort)
      }
    }
  }
</script>