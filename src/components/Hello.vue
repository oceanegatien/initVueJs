<template>
  <div class="hello-world">
    <h1>{{msg}}</h1>
    <h5>{{subtitle}}</h5>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Hello World',
      subtitle: 'subtitle'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
