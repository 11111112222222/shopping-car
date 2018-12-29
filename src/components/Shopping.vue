<!-- 模拟购物车 -->

<template>
  <div id="shopping">
    <el-table ref="singleTable" :data="tableData" highlight-current-row style="width: 100%">
      <el-table-column type="index" width="50"></el-table-column>
      <el-table-column property="goodsName" label="商品名称" width="120"></el-table-column>
      <el-table-column property="price" label="商品单价" width="120"></el-table-column>
      <el-table-column property="number" label="购买数量" width="200">
        <template slot-scope="scope">
          <el-button size="mini"  @click="handleSubtract(scope.$index, scope.row)">-</el-button>
          {{scope.row.number}}
          <el-button size="mini" type="danger" @click="handleAdd(scope.row)">+</el-button>
        </template>
      </el-table-column>
      <el-table-column label="操作" width="120">
        <template slot-scope="scope">
          <el-button size="mini" @click="remove(scope.$index)">移除</el-button>
        </template>
      </el-table-column>
    </el-table>

    <div style="margin-top:20px;float:left">总价：&nbsp;&nbsp;{{calculate}}</div>
  </div>
</template>

<script>
export default {
  name: "shopping",
  data() {
    return {
      totalMoney: 0,
      tableData: [
        {
          goodsName: "iphone7",
          price: 5555,
          number: 1
        },
        {
          goodsName: "iphone7",
          price: 5555,
          number: 1
        },
        {
          goodsName: "iphone7",
          price: 5555,
          number: 1
        },
        {
          goodsName: "iphone7",
          price: 5555,
          number: 1
        }
      ],
      currentRow: null
    };
  },

  components: {},

  computed: {
    calculate: function() {
      var sum = 0;
      for (var i = 0; i < this.tableData.length; i++) {
        sum += this.tableData[i].price * this.tableData[i].number;
      }
      return sum;
    }
  },

  methods: {
    handleSubtract(index, row,event) {
      // var event = event ? event : window.event; 
      // var obj=event.srcElement ? event.srcElement : event;
      // if (row.number ==1) {
      //   obj.setAttribute("disabled", true);
      // } else if(row.number==2){
      //   row.number-=1;
      //   obj.setAttribute("disabled", true);
      // }else{
      //   console.log("进来过");
      //   obj.setAttribute("disabled", false);
      //   row.number-=1;
      // }
      if(row.number>1){
        row.number-=1;
      }
    },
    handleAdd(row) {
      row.number += 1;
    },
    remove(index) {
      this.tableData.splice(index, 1);
    }
  }
};
</script>
<style>
</style>