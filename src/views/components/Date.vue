<template>
  <div>
    <DatePicker
        :value="month"
        type="month"
        placeholder="Select month"
        style="width: 200px"
        @on-change="timeChange"
    ></DatePicker>
    <Button type="primary" @click="handleClick">显示</Button>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        month: '2019-2'
      }
    },
    methods: {
      handleClick () {
        console.log(this.month);
      },
      timeChange (e) {
        this.month = e;
      }
    }
  }
</script>

<style>

</style>