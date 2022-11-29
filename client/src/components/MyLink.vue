<template>
    
    <div class="fs-5" v-if="!this.$store.state.isAuthenticated">
        <router-link :to="{ name: 'Login' }" style="text-decoration: none"> 
            Đăng nhập
        </router-link>
        để sử dụng chức năng này.
    </div>
  
    <div class="" v-else>
        <h3>History ShortenerLink</h3>
        <table class="table table-striped table-borderes" style="margin: auto">
            <thead>
                <tr>
                    
                    <th style="width:15%">ShortUrl</th>
                    <th scope="col">URL</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="s in test" :key="s._id">
                    <td ><a>{{s.shortURL}}</a></td>
                    <td>{{s.longURL}}</td>
                    
                </tr>
            </tbody>
        </table>
        
    </div>
    
</template>
<script>
import axios from "axios";

export default {
   
    data: () => {
      return {
        link: [],
        test: {},
      };
    },
    
    computed: {
        
        getPhone() {
          return this.$store.getters.getPhone
        },
    },

  mounted(){
    const  phone =this.$store.getters.getPhone;
    axios.post("http://localhost:5000/test",{phone})

    .then((response) => {
        console.log(response.data);
        this.test= response.data
        
    })
    .catch((error)=>{
        console.log(error)
    })
  }  
  
  
};


</script>

<style scoped>
.page {
    text-align: left;
    max-width: 750px;
}
</style>    