<template>
  <q-page padding>
    <button @click="count++">{{count}}</button>

    <input
      v-model="message"
      @keyup.esc="clearMessage"
      :class = "erroStyle"
    />
    <button @click="clearMessage"> Clear </button>
    <div>{{message.length}}</div>

    <h6 v-show="message.length">Tipying...</h6>
    <h5 v-if="message.length"> {{ message }}</h5>
    <h6 v-else> No message entered</h6>
    <hr/>
    <h6>Uppercase Message: {{upperCaseMessage}}</h6>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data() {
    return {
      message: 'First vue application',
      count: 0
    }
  },
  methods: {
    clearMessage() {
      this.message = ''
    },
    handleKeyup(e) {
      //console.log(e)
      if (e.keyCode == 27) this.clearMessage()
    }
  },
  computed:{
    upperCaseMessage() {
      console.log('upperCaseMessage fired')
      return this.message.toUpperCase()
    },
    erroStyle() {
      return this.message.length > 22 ? 'erro' : ''
    }
  },
  beforeCreate() {
    console.log('beforeCreate fired')
  },
  created() {
    console.log('created fired')
  },
  beforeMount() {
    console.log("beforeMount fired");
  },
  mounted() {
    console.log("mouted fired");
  },
  beforeUnmount() {
    console.log("beforeUnmount fired");
  },
  unmounted() {
    console.log("unmounted fired");
  }
})
</script>
<style>
.erro {
  background-color: pink;
  color: red;
}
</style>
