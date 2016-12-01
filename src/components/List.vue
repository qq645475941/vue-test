<template>
    <div class="panel  panel-primary">
  <!-- Default panel contents -->
  <div class="panel-heading">今日行程列表</div>
  <div class="panel-body">
    <div class="input-group">
      <span class="input-group-addon">添加行程</span>
      <input type="text" class="form-control" placeholder="输入后按回车确定"  v-model="newItem" @keyup.enter="addNew">
    </div>
  </div>
  <table class="table">
    <tr>
      <th>#</th>
      <th>行程列表</th>
      <th></th>
      <th>状态</th>
      <th></th>
      <th>删除</th>
    </tr>
    <tr v-for="item ,index in items">
      <td>{{index+1}}</td>
      <td>{{item.things}}<td>
      <td  @click="finished(item)">{{item.state}}<td>
      <td @click="delate(item)">删除<td>
    </tr>  
  </table>
</div>

</template>

<script>
export default {
  name: 'list',
  data:function(){
    return {
      items:[
      {
      things:"面试",
      state:"未完成",
      isFinished:false,
      isDelate:false
      }
      ],
      newItem:""
    }
  },
  methods:{
    addNew:function(){ 
      this.newItem&&this.items.push({
          things:this.newItem,
          state:"未完成",
          isFinished:false,
          isDelate:false
      })

       this.newItem="";
    },
    delate:function(item){
        if(item.isDelate){
    var idx=this.items.indexOf(item);
        this.items.splice(idx,1);
        }
    },
    finished:function(item){
        item.state="完成";
        item.isisFinished=true;
        item.isDelate=true;
    }
  }
}
</script>
<style scoped>

</style>
