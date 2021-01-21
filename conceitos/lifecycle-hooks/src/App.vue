<template>
  <h1>Lifecycle Hooks</h1>
</template>

<script>
import { onMounted } from 'vue'

/*
export default {
  mounted() {
    console.log('Foi montado options API')
  }
}
*/

export default {
  setup() {
    onMounted(() => {
      console.log('Foi montado composition API')
    })
  }  
}
</script>