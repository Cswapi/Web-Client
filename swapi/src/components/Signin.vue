<template>
  <div id="login">
    <p>
      <router-link to="/Signup">SIGN UP</router-link>
    </p>
    <p>
      <input id="username" type="text" placeholder="username" v-model="usr"></input>
    </p>
    <p>
      <input id="password" type="password" placeholder="password" v-model="psw"></input>
    </p>
    <p>
      <button v-on:click="post">SIGN IN</button>
    </p>
    <p>
      <a href="#/Search" v-on:click="guessMode()">Unregistered login</a>
    </p>
  </div>
</template>

<script>
export default {
  name: 'Signin',
  data: function() {
    return {
      usr: "",
      psw: ""
    };
  },
  methods: {
    post: function() {
      this.$http.post("http://localhost:8080/login", 
        {
          username:this.usr, 
          password:this.psw
        },
        {
          withCredentials:true
        }
        ).then(
        function(res) {
          if(res.ok) {
            var strContent = JSON.stringify(res.data);
            var jsonContent = JSON.parse(strContent);
            //console.log("token:",jsonContent["token"]);
            $cookies.set("LogInUser", jsonContent["token"]);
            this.$router.push({path:"/Search"});
          }
          else {
            alert("Error: Sign in error!");
          }
        },
        function() {
          alert("error");
        });
    },

    guessMode: function() {
      $cookies.set("LogInUser", "guest");
    }
  }
}
</script>
