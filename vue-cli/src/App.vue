<template>
  <!-- 오직 하나의 element만 있어야 한다. -->
  <div>
    <!-- <app-header v-bind:프롭스 속성 이름="상위 컴포넌트의 데이터 이름"></app-header> -->
    <app-header 
      v-bind:propsdata="str"
      v-on:renew="renewStr"></app-header>
  </div>
</template>

<script>
import AppHeaer from './components/AppHeader.vue';


// 
// new Vue({
//   data: {

//   }
// })
export default {
  // 컴포넌트를 재사용하겠단 의지, 컴포넌트를 재사용 할 확률이 높다. 
  // 때문에 여러개의 컴포넌트에서 동일한 값을 공요(참조)하면 안되기 때문에 
  // 아래와 같이 function() 에 return 으로 새 객체를 반환해주는 규칙을 사용해야 한다. 

  data: function() {
    return {
      str: 'Header'
    }
  },
  components: {
    'app-header': AppHeaer
  },
  methods: {
    renewStr: function() {
      this.str = 'hi';
    }
  }
}
</script>
  
<style>

</style>