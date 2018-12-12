<template>
  <div>
    <Tabs value="name1">
      <TabPane label="标签一" name="name1">
        <div class="flex">
          <AutoComplete
              v-model="value2"
              @on-search="handleSearch2"
              placeholder="input here"
              style="width:200px">
            <Option v-for="item in data2" :value="item" :key="item">{{ item }}</Option>
          </AutoComplete>
        </div>
      </TabPane>
      <TabPane label="标签二" name="name2">标签二的内容</TabPane>
      <TabPane label="标签三" name="name3">标签三的内容</TabPane>
    </Tabs>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        value2: '',
        data2: []
      }
    },
    mounted(){
      this.value2 = '中文';
    },
    methods: {
      handleSearch2 (value) {
        this.data2 = !value || value.indexOf('@') >= 0 ? [] : [
          value + '@qq.com',
          value + '@sina.com',
          value + '@163.com'
        ];
      }
    }
  }
</script>

<style lang="less">
  .flex{
    display: flex;
    height: 100vh;
    div{
      margin: auto;
    }
  }
</style>