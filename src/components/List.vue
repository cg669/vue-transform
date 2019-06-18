<template>
  <div class="tree-box">
      <ul>
          <li v-for="value in listData" :key="value.id" class="item">
              <span>{{value.label}}</span>
              <el-button type="danger" icon="el-icon-delete" circle @click="$emit('delete',value.id)"></el-button>
          </li>
      </ul>
  </div>
</template>
<script>

export default {
    props: {
        listData: Array
    },

    methods: {
      
    },

    data() {
      return {
        
      };
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul{
    padding: 10px;
    margin: 0;
}
li{
    margin: 5px 0;
    padding: 5px;
}
.tree-box{
    width: 300px;
    max-height: 400px;
    overflow-y: auto;
    background-color: #efefef;
}
.item{
    background-color: #fff;
    display: flex;
    justify-content: space-between;
    line-height: 40px;
}
</style>
