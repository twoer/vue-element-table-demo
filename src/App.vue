<template>
  <div id="app">
   <template>
    <el-row>
      <el-col :span="24">
        <el-form :inline=true :model="formConfig" class="demo-form-inline">
          <el-form-item label="最大行高">
            <el-select v-model="formConfig.maxHeight" placeholder="请选择最大行高">
              <el-option label="40px" value="40"></el-option>
              <el-option label="60px" value="60"></el-option>
              <el-option label="80px" value="80"></el-option>
              <el-option label="100px" value="100"></el-option>
              <el-option label="300px" value="300"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item label="字体大小">
            <el-select v-model="formConfig.fontSize" placeholder="请选择字体大小">
              <el-option label="10px" value="10"></el-option>
              <el-option label="12px" value="12"></el-option>
              <el-option label="14px" value="14"></el-option>
              <el-option label="16px" value="16"></el-option>
            </el-select>
          </el-form-item>
        </el-form>
      </el-col>
    </el-row>

    <el-row >
      <el-col :span="24">
        <el-table
          ref="table"
          :data="tableData"
          height="100%"
          border
          style="width: 100%">
          <el-table-column
            prop="date"
            label="日期"
            width="180"
            fixed>
          </el-table-column>
          <el-table-column
            prop="address"
            label="地址"
            width="250">
            <template slot-scope="scope">
              <addressCell :row="scope.row" :column="scope.column" :config="formConfig" ></addressCell>
            </template>
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180">
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180">
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180">
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180">
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180">
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180">
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180">
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180">
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180">
          </el-table-column>
        </el-table>
      </el-col>
    </el-row>
  </template>
  </div>
</template>

<script>
import addressCell from './components/address-cell.vue'

export default {
  name: 'app',
  data () {
    return {
      formConfig: {
        maxHeight: '60',
        fontSize: '14'
      },
      tableData: [{
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄 end'
      }, {
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄'
      },
      {
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄上海市普陀区金沙江路 1518 弄'
      }]
    }
  },
  created () {
  },
  components: { addressCell },
  methods: {}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.el-form
{
  text-align: left;
}
.address-wrap
{
  /*display: -webkit-box;-webkit-box-orient: vertical;-webkit-line-clamp: 3;*/
/*overflow: hidden;*/
/*height: 60px;*/
  /*white-space: nowrap;*/
  /*text-overflow: ellipsis;*/
  /*overflow: hidden;*/
}
</style>
