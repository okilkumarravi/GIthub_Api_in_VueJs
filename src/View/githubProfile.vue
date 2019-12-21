<template>
<div class="github-profile">
    Github profile Demo
<div>
    <div class="ui centered  card">
  <div class="image">
    <img v-bind:src="data.avatar_url" alt="profile-image">
  </div>
  <div class="content">
    <a class="header" :href="data.html_url">{{data.name}}</a>
    <div class="meta">
      <span class="date">Joined in {{data.created_at.slice(0,10)}}</span>
    </div>
    <div class="description">
      {{data.bio}}
    </div>
  </div>
  <div class="extra content">
    <a>
      <i class="user icon"></i>
     {{data.followers+10}}
    </a>
  </div></div>
</div>
</div>
    
</template>
<script> 
import axios from 'axios';
export default {
    name : 'githubProfile',
    data() {
        
        return  {
data : null
        }
    },
    mounted(){
        axios.get('https://api.github.com/users/{userName}').then(Response => {         //e.g - okilkumarravi
            this.data = Response.data;
        })
    }
}
</script>
<style scoped>
.github-profile{
    display: block;
    margin-left: auto;
text-align: center;
}

</style>