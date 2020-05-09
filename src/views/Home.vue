<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/book1.png">
    <HelloWorld msg="Welcome to Your Library"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>
