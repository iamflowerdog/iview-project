<template>
  <div class="flex">
    <Select style="width:200px" remote filterable @on-change="handleChange">
      <Option value="1">1111</Option>
      <Option value="2">22222</Option>
      <Option value="3">
        <AddCus></AddCus>
      </Option>
    </Select>
  </div>
</template>

<script>
  import AddCus from './AddCus.vue';
  export default {
    components: {
      AddCus
    },
    methods: {
      handleChange (value) {
        console.log(value);
        if (value === '3') {
          return
        }
      }
    }
  }
</script>

<style>

</style>