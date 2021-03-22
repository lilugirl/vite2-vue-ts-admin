<template>
  <h1>{{ msg }}</h1>
  <button @click="increment">Press me</button>
  {{counter}}
</template>

<script lang="ts">
import { ref, defineComponent, computed } from 'vue'
import { useStore } from 'vuex'
import { key } from '../store'
export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: {
      type: String,
      required: true
    }
  },
  setup: () => {
    const count = ref(0)
    const store=useStore(key);
    const increment=()=>store.dispatch('increment');
    const counter=computed(()=>store.state.count)
    return { count,counter,increment }
  }
})
</script>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
