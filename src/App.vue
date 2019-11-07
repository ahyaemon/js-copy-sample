<template>
  <div id="app">
    <h1>Copy Sample</h1>
    <div>
      <textarea></textarea>
    </div>
    <div>
      <textarea readonly @click="copySample1">{{ text1 }}</textarea>
    </div>
    <div>
      <textarea id="copy-area" :readonly="isReadOnly" @click="copySample2">{{ text2 }}</textarea>
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
  private isReadOnly = true

  copySample1() {
    navigator.clipboard.writeText(this.text1)
  }

  copySample2() {
    this.isReadOnly = false

    const copyArea = document.getElementById('copy-area')! as HTMLInputElement
    copyArea.select()
    document.execCommand('copy')

    this.isReadOnly = true
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
