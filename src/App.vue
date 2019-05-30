<template>
  <div id="app">
   <template>
    <el-row>
      <el-col :span="24">
        <el-alert
          title="需求：地址列 可以设置 Row 最大高度，字体可以设置大小，实际显示行数动态计算，内容溢出时显示 ... 并增加 Tip，其实主要问题是 有 Fixed 列时，其他 Row 单纯通过 CSS 控制，Fixed 列无法同步其高度"
          type="warning" effect="dark">
        </el-alert>

      </el-col>
    </el-row>

    <el-tabs v-model="tabName"  type="border-card">
      <el-tab-pane label="正常 Demo" name="normal">
        <el-row>
          <el-col :span="24">
            <el-alert
              type="info">
              <div slot="title">
                有点蠢的 <el-link target="_blank" href="https://github.com/twoer/vue-element-table-demo/blob/master/src/components/address-cell.vue" type="primary">实现代码</el-link>
              </div>
            </el-alert>

          </el-col>
        </el-row>
        <el-row>
          <el-col :span="24">
            <el-form :inline=true :model="formConfig" class="demo-form-inline" size="small">
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
              height="500px"
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
      </el-tab-pane>
      <el-tab-pane label="Bug Demo" name="bug">
        <el-row>
          <el-col :span="24">
            <el-alert
              title="地址列 是通过 -webkit-line-clamp: 3 强制控制在3行，Fixed 列无法同步其高度"
              type="info">
            </el-alert>

          </el-col>
        </el-row>
        <el-row >
          <el-col :span="24">
            <el-table
              ref="table"
              :data="tableData"
              height="500px"
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
                  <div class="address-css-cell">{{scope.row.address}}</div>
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
      </el-tab-pane>
    </el-tabs>
  </template>
  </div>
</template>

<script>
import addressCell from './components/address-cell.vue'

export default {
  name: 'app',
  data () {
    return {
      tabName: 'normal',
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
.el-row + .el-row
{
  margin-top: 10px;
}
.el-tabs
{
  margin-top: 10px;
}
.el-tabs .el-tab-pane
{
  padding: 8px;
}
.el-form
{
  text-align: left;
}
.address-css-cell
{
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  overflow: hidden;
}
</style>
