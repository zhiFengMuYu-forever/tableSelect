<template>
  <div class="home">
    <el-button type="info" plain style="margin: 1px 10px" @click="dialogFormVisible = true">添加</el-button>
    <!-- 添加 -->
    <el-dialog title="添加" :visible.sync="dialogFormVisible">
      <el-form :model="form">
        <el-form-item label="地址" :label-width="formLabelWidth">
          <!-- Popover 弹出框 -->
          <el-popover placement="bottom-start" width="400px" trigger="click">
            <el-table :data="tableSelectData" @row-click="tableSelectRow">
              <el-table-column fixed type="index" width="50" />
              <el-table-column prop="date" label="日期" width="100"></el-table-column>
              <el-table-column prop="name" label="姓名" width="100"></el-table-column>
              <el-table-column prop="address" label="地址" width="300"></el-table-column>
            </el-table>
            <el-input
              autocomplete="off"
              slot="reference"
              v-model="form.address"
              clearable>
            </el-input>
          </el-popover>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">取 消</el-button>
        <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
      </div>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      tableSelectData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄",
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄",
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄",
        },
      ],
      dialogFormVisible: false,
      form: {
        address: "",
      },
      formLabelWidth: "120px",

      
    };
  },
  methods: {
    tableSelectRow(row){
      this.form.address=row.address;
    },
  },
};
</script>