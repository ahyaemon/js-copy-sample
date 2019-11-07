<template>
  <div id="app">
    <h1>Copy Sample3</h1>
    <p>{{ userAgent }}</p>
    <p>isIOS: {{ isIOS }}</p>
    <div>
      <textarea></textarea>
    </div>
    <div>
      <textarea readonly @click="copySample1">{{ text1 }}</textarea>
    </div>
    <div>
      <textarea id="copy-area" :readonly="isReadOnly" @click="copySample2">{{ text2 }}</textarea>
    </div>
    <div>
      <textarea id="copy-area3" :readonly="isReadOnly" @click="copySample3">{{ text3 }}</textarea>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from './components/HelloWorld.vue';

@Component({
  components: {
    HelloWorld,
  },
})
export default class App extends Vue {

  private text1 = 'text1';
  private text2 = 'text2';
  private text3 = 'text3';
  private isReadOnly = true;
  private userAgent = '';

  private mounted() {
    this.userAgent = navigator.userAgent;
  }

  private copySample1() {
    if (this.isIOS) {
      const yourCode: any = document.getElementById('copy-area1');
      const range = document.createRange();
      range.selectNode(yourCode);
      window.getSelection()!!.addRange(range);
      document.execCommand('copy');
    } else {
      navigator.clipboard.writeText(this.text1);
    }
  }

  private copySample2() {
    if (this.isIOS) {
      const yourCode: any = document.getElementById('copy-area2');
      const range = document.createRange();
      range.selectNode(yourCode);
      window.getSelection()!!.addRange(range);
      document.execCommand('copy');
    } else {
      navigator.clipboard.writeText(this.text2);
    }
  }

  private copySample3() {
    const yourCode: any = document.getElementById('copy-area3');
    const range = document.createRange();
    range.selectNode(yourCode);
    window.getSelection()!!.addRange(range);
    document.execCommand('copy');
  }

  get isIOS() {
    return /iP(hone|(o|a)d)/.test(this.userAgent);
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
