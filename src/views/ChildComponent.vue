<template>
  <div>
    <p>{{ alertMessage }}</p>
    {{ propsMessage }}
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch} from 'vue-property-decorator';

// @Component : Vue 가 인식할 수 있는 형태로 변환하는 것을 의미한다.
@Component
export default class Child extends Vue {

  // 'readonly' : 대상 멤버를 읽기 전용으로 한정하겠다는 한정자, @Prop이나 @Model 등에 readonly 한정자를 선언하는 것이 좋다.
  // '!' : null / Undefined를 설정할 수 없음을 나타내는 것이다. ( NonNullAssersion 오퍼레이터)
  // '?' : 타입 영역 정의, null / undefined도 가능하다

  // propsData? : string 에서 '?'무엇일까
  // propsMessage 받는 데이터는 string type만 허용한다.
  @Prop()
  private propsMessage?: string;

  public alertMessage: string = '';

  // todo: 확인할 것 vue의 인스턴스의 Watch와 동일합니다.
  @Watch('propsMessage')
  public updateMessage() {
    console.log("==== Watch ====");
    this.alertMessage = 'alertMessage';
    // this.alertMessage = 1;
    // this.alertMessage = null;
    // this.alertMessage = undefined;
    // this.alertMessage = this;
  }
}
</script>
