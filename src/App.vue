<template>
  <div id="app">
    <h1>Copy Sample3</h1>
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

  private text1 = 'text1'
  private text2 = 'text2'
  private text3 = 'text3'
  private isReadOnly = true

  copySample1() {
    navigator.clipboard.writeText(this.text1).then((res) => {
      alert('then')
    }).catch((e) => {
      alert('catch')
      var yourCode: any = document.getElementById('copy-area');
      var range = document.createRange();
      range.selectNode(yourCode);
      window.getSelection()!!.addRange(range);
      document.execCommand('copy');
    })
  }

  copySample2() {
    this.isReadOnly = false

    const copyArea = document.getElementById('copy-area')! as HTMLInputElement
    copyArea.select()
    document.execCommand('copy')

    this.isReadOnly = true
  }

  copySample3() {
    var yourCode: any = document.getElementById('copy-area3');
    var range = document.createRange();
    range.selectNode(yourCode);
    window.getSelection()!!.addRange(range);
    document.execCommand('copy');
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
