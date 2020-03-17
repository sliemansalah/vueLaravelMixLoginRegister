<template>
  <div class="row">
    <div class="card ml-15" style="width: 18rem;">
  <div class="card-body text-center">
    <h5 class="card-title">Customers</h5>
    <router-link to="/customers"><span class="fs-28">{{ customersCount }}</span></router-link>
  </div>
</div>
 <div class="card ml-15" style="width: 18rem;">
  <div class="card-body text-center">
    <h5 class="card-title">Users</h5>
    <router-link to="/users"><span class="fs-28">{{ usersCount }}</span></router-link>
  </div>
</div>
  </div>
</template>
<script>
  import axios from 'axios'
export default {
  data(){
    return {
      customersCount:0,
      usersCount:0,
    }
  },
  mounted(){
    let customers = [];
    axios.get('/api/customers').then(res=> {
      customers = res.data.data
        this.customersCount = customers.length
    }),
    axios.get('https://reqres.in/api/users/').then(res=> {
      this.usersCount = res.data.data.length
    });
  }
}
</script>

<style>
.fs-28{
  font-size: 28px;
}
.ml-15{
  margin-left: 15px;
}
</style>
