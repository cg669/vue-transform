<template>
  <div class="container">
    <Tree :treeData="dataList" ref="treeBox"/>
    <div class="add-btn">
      <el-button type="primary" @click="addData()">主要按钮</el-button>
    </div>
    <List :listData="listData" @delete="handleDelete"/>
  </div>
</template>

<script>
import { dataList } from '../constant'
import Tree from './Tree';
import List from './List';
export default {
  name: 'HelloWorld',
  data(){
    return {
      dataList,
      listData:[]
    }
  },
  methods:{
    addData(){
      const nodes = this.$refs.treeBox.getCheckedNodes();
      // console.log(nodes)
      if(nodes && nodes.length > 0){
        this.listData = nodes.filter( el => !el.children).sort( (a,b) => a.id - b.id > 0)
      }
      // console.log(nodes);
    },
    handleDelete(id){
      // console.log(id,'id')
      this.$refs.treeBox.setChecked(id,false);
      this.listData = this.listData.filter( item => item.id !== id)
    }
  },
  props: {
    msg: String
  },
  components:{
    Tree,
    List
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container{
  display: flex;
}
.add-btn{
  width: 200px;
  text-align: center;
  line-height: 300px;
}
</style>
