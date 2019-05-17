<template>
  <div class="flex">
    <div
        v-for="(item, index) in list"
        :class="['checkbox', { active: item.checked }]"
        @click="handleChange(item.id)">
      test
    </div>
    <Radio></Radio>
  </div>
</template>

<script>
  export default {
    name: 'ChangeClass',
    data () {
      return {
        value: 'zfb',
        list: []
      }
    },
    mounted () {
      this.fetchList();
    },
    methods: {
      fetchList () {
        this.list = [
          {
            name: '支付宝支付',
            id: 'zfb'
          },
          {
            name: '微信支付',
            id: 'wChat'
          }
        ];
        this.updateValue();
      },
      updateValue () {
        let currentValue = this.value;
        this.list.forEach((item, index) => {
          this.$set(this.list, index, Object.assign({}, item, {checked: item.id === currentValue}))
        });
      },
      handleChange (index) {
        this.value = index;
        this.updateValue();
      }
    }
  }
</script>

<style lang="less" scoped>
  .checkbox{
    width: 100px;
    height: 100px;
    background: #c3c3c3;
    cursor: pointer;
    &.active {
      background: rebeccapurple;
    }
  }
</style>