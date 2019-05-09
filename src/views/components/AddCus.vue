<template>
  <span>
    <Button @click="handleClick">新建客户</Button>
    <Modal v-model="visible">
      test
    </Modal>
  </span>
</template>

<script>
  export default {
    data () {
      return {
        visible: false
      }
    },
    methods: {
      handleClick () {
        this.visible = true
      }
    }
  }
</script>

<style>

</style>