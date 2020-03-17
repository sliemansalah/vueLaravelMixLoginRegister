<template>
  <div>
      <h3>User Details</h3>
      <br><br>
      <h5>Main Data</h5>
      <br>
      <ul>
          <div  v-for="(main,key)  in userDetails.data" :key="key">
              <li v-if="key!=='avatar'">
            <span>
            {{key}} : {{main}} <br>
            </span>
          </li>
          <li v-else>
              <br>
              <img :src="main" alt="">
          </li>
          </div>
          
      </ul>
      <hr>
      <h5>AD Data</h5>
      <ul>
          <li v-for="(det,key) in userDetails.ad" :key="key">
             {{key}} : {{det}} <br>
          </li>
      </ul>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    data(){
        return {
            userDetails:[]
        }
    },
    mounted(){
         axios.get("https://reqres.in/api/users/"+this.$route.params.id).then(res=>{
        this.userDetails = res.data;
        console.log(this.userDetails);
      })
    }
}
</script>

<style>

ul li:last-child{
    list-style: none;
}
</style>