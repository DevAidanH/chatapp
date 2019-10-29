<template>
  <div class="welcome container">
    <div class="card">
      <div class="card-content center-align">
        
        <h2 class="pink-text">Welcome</h2>
        <form @submit.prevent="enterChat">
          <label for="name">Enter your name:</label>
          <input name="name" type="text" v-model="name" autocomplete="off">
          <p class="red-text">{{ feedback }}</p>
          <button class="btn pink">Enter Chat</button>
        </form>
      </div>
    </div>
  </div> 

</template>

<script>
export default {
  name: 'Welcome',
  data () {
    return {
      name: null,
      feedback: null
    }
  },
  methods:{
    enterChat(){
      if(this.name){
        this.feedback = null
        this.$router.push({ name: "Chat", params: {name: this.name} })
      }
      else{
        this.feedback = "You must enter a name to join"
      }
    }
  }
}
</script>

<style>
body{
  background-image: url("~@/assets/background.png");
  background-repeat: no-repeat;
  background-position: 70% 30%;
  background-size: 100vw;
}
.welcome{
  max-width: 400px;
  margin-top: 100px; 
}
.welcome h2{
  font-size: 3em
}
.welcome .btn{
  margin: 30px auto
}
.welcome .card, .chat .card {
  box-shadow: 15px 15px 10px #000;
  border-radius: 10px
}
@media (max-width: 768px) {
  body{
    background: #BD1C60
  }
  .welcome .card, .chat .card{
    box-shadow: 0 0 0 #000
  }
}
</style>
