<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Hello, Vue.js + TypeScript App"/>
    <h3>컴퍼넌트 생성</h3>
    <message></message>
    <hr>
    <h3>Watch 감지</h3>
    <child-component :propsMessage="message"></child-component>
    <button @click="onChange">버튼</button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from './components/HelloWorld.vue';
import Message from '@/components/Message.vue';
import Child from '@/views/ChildComponent.vue';

@Component({
  components: {
    HelloWorld,
    Message, Child
  },
})
export default class App extends Vue {
  public message: string = '안녕하세요.';

  public onChange() {
    this.message = '변경됬습니다.';
  }
}
</script>

<style lang="stylus">
#app
  font-family Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px
</style>
