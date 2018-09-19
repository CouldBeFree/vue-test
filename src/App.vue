<template>
  <div id="app">
    <Modal/>
  </div>
</template>

<script>
    import Modal from './components/modal'

    export default {
        name: 'app',
        components:{
            Modal
        }
    }
</script>

<style lang="scss">
  .test{
    margin-top: 400px;
  }
</style>
