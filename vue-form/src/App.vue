<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <!-- input 의 id를 username 으로 하고 label의 이름을 username으로 하면 label은 input을 바라봄-->
      <label for="username">id: </label> 
      <!-- input  내용을 자동으로 username 에 반영하는 v-model-->
      <input id="username" type="text" v-model="username">
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password">
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
  import axios from 'axios';

export default {
  data: function() {
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    submitForm: function() {
      // 자바스크립트에서 
      // form 은 어떤 정보를 제출하고 해당 페이지로 넘어가는 특성이 있기 때문에 그것을 
      // 막기 위해 preventDefault()를 사용하여 새로고침을 막는다. 
      // event.preventDefault();
      // 하지만, vue 에서는 form 태그에서 v-on:submit.prevent 를 통하여 해당 기능을 수행할 수 있다.
      console.log(this.username, this.password);
      var url = 'https://jsonplaceholder.typicode.com/users'
      var data = {
        username: this.username,
        password: this.password
      }
      axios.post(url, data)
        .then(function(response) {
          console.log(response);
        })
        .catch(function(error) {
          console.log(error);
        }); //http 프로토콜을 이용한 http 통신 라이브러리 : 어떠한 데이터를 주고 받기 위해 사용
                    // post 는 어떠한 데이터를 생성하거나 조작할 때, 사용하는 http method
    }
  }
}
</script>

<style>

</style>