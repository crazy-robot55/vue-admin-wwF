<template>
    <div>
        <div>
            <el-button size="small" type="primary">添加 </el-button>

            <el-button size="small" type="danger">批量删除 </el-button>
        </div>
        <el-table :data="employees">
            <el-table-column label="编号" prop="id"></el-table-column>
            <el-table-column label="姓名" prop="real name"></el-table-column>
            <el-table-column label="性别" prop="gender"></el-table-column>
            <el-table-column label="手机号" prop="telphone"></el-table-column>
            <el-table-column label="身份证号" prop="idcard"></el-table-column>
            <el-table-column label="银行卡号" prop="bankcard"></el-table-column>
            <el-table-column label="操作">
                <template v-slot="slot">
                   <a href="" @click.prevent="toDeleteHandler(slot.row.id)">删除</a>
                   <a href="" @click.prevent="toUpdateHandler(slot.row)">修改</a>
                </template>
            </el-table-column>
        </el-table>
        
        <el-pagination layout="prev, pager, next" :total="50">
        </el-pagination>

        <el-dialog
      title="录入员工信息"
      :visible.sync="visible"
      width="60%">
      <span>这是一段信息</span>
      <span slot="footer" class="dialog-footer">
        <el-button size="small" @click="closeModalHandler">取 消</el-button>
        <el-button size="small" type="primary" @click="closeModalHandler">确 定</el-button>
      </span>
    </el-dialog>
    </div>
</template>

<script>
export default {
    data(){
       
       return{
           visible:false,

       }
    },methods:{
        totoDeleteHandler(id){
            this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning'
      }).then(() => {
        this.$message({
          type: 'success',
          message: '删除成功!'
        });
      })
        },
        toUpdateHandler(){
        this.title="修改员工信息"
        this.visible = true;
    },
        closeModalHandler(){
      this.visible = false;
    },
        toAddHandler(){
        this.title="录入员工信息"
        this.visible = true;
    }
  }
}
    

</script>

<style scoped>

</style>