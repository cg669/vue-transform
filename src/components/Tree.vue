<template>
  <div class="tree-box">
      <el-input
        placeholder="输入关键字进行过滤"
        v-model="filterText">
        </el-input>

        <el-tree
            class="filter-tree"
            show-checkbox
            :data="treeData"
            node-key="id"
            :props="defaultProps"
            default-expand-all
            :filter-node-method="filterNode"
            ref="tree">
        </el-tree>
  </div>
</template>
<script>

export default {
    props: {
        treeData: Array
    },
    watch: {
      filterText(val) {
        this.$refs.tree.filter(val);
      }
    },

    methods: {
      setChecked(...arg){
        this.$refs.tree.setChecked(...arg)
      },
      getCheckedNodes() {
        return this.$refs.tree.getCheckedNodes()
      },
      filterNode(value, data) {
        if (!value) return true;
        return data.label.indexOf(value) !== -1;
      }
    },

    data() {
      return {
        filterText: '',
        defaultProps: {
          children: 'children',
          label: 'label'
        }
      };
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.tree-box{
    width: 300px;
    max-height: 400px;
    overflow-y: auto;
}
.el-tree{
    background-color: #efefef;
}
</style>
