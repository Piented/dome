<template>
  <div class="home">
    <el-row>
      <el-button @click="getList">默认按钮</el-button>
    </el-row>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: "HomeView",
  methods:{
    getList(){
      console.log('11111')
      this.axios.get('http://localhost:3312/user/getList',{
        params:{
          page:this.query.page,
          size:this.query.size,
          name:this.query.name,
          phone:this.query.phone,
          city:this.query.city,
        }
      }).then((resp)=>{
        console.log(resp);
        this.tableData = resp.data.content.list;
        this.total = resp.data.content.total;
      })
    }
  }
};
</script>
