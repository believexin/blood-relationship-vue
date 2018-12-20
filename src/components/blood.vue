<template>
  <div id="blood">
    <el-input placeholder="place input scheamname" v-model="schema"></el-input>
    <el-input placeholder="place input tablename" v-model="tablename"></el-input>
    <el-button type="primary" v-show="isEdit" class="save-btn" @click="getBloodRelatrionship(schema,tablename)">查询</el-button>

		<el-tree v-show="isShow" background-color="#545b64" text-color="#fff" 
      active-text-color="#ffd04b"  class="filter-tree" 
      :default-expanded-keys="defaultKey"  node-key="id" 
      :data="data2" :props="defaultProps"  
      :filter-node-method="filterNode" ref="tree2" 
      @node-click="nodeClick">
		</el-tree>
  </div>
</template>

<script>
export default {
  name: 'Blood',
   data(){
    return{
      ship:'',
      tablename:"",
      schema:"",
      isShow:false,
      data2:{},
      defaultProps: {
	      children: 'children',
	      label: 'viewname'
	    }
    }
   },
   methods:{
     getBloodRelatrionship:function(schema,tablename){
        this.$nextTick(function() {
          this.$axios.get(this.HOST + "/api/bloodRatelationShip?schema="+ schema + "&tablename="+ tablename).then(res =>{
            this.ship = res.data;
            this.isShow = true;
          });
        })
     }
   },
   mounted(){
    
  }
}
</script>

<style>

</style>