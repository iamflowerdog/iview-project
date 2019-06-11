<template>
  <div>
    <Tabs value="name7" :animated="false">
      <TabPane label="标签一" name="name1">
        <div class="flex">
          <AutoComplete
              v-model="value2"
              @on-search="handleSearch2"
              @on-select="handleSelect"
              placeholder="input here"
              :label-in-value="true"
              style="width:200px">
            <Option v-for="item in data2" :label="item.name" :value="item.id" :key="item.id"></Option>
          </AutoComplete>
        </div>
      </TabPane>
      <TabPane label="标签二" name="name2">
        <div class="flex">
          <Select
              v-model="model13"
              filterable
              remote
              :remote-method="remoteMethod1"
              style="width:200px"
          >
            <Option v-for="(option, index) in options1" :value="option.value" :key="index">{{option.label}}</Option>
          </Select>
        </div>

      </TabPane>
      <TabPane label="标签三" name="name3">
        <Date></Date>
      </TabPane>
      <TabPane label="新建客户slot" name="name4">
        <ESelect></ESelect>
      </TabPane>
      <TabPane label="测试class不更改" name="name5">
        <ChangeClass></ChangeClass>
      </TabPane>
      <TabPane label="row_flex_justify" name="name6">
        <Row_Flex></Row_Flex>
      </TabPane>
      <TabPane label="input" name="name7">
        <InputA></InputA>
      </TabPane>
    </Tabs>
  </div>
</template>

<script>
  import Date from './components/Date.vue'
  import ESelect from './components/ESelect.vue'
  import ChangeClass from './components/ChangeClass.vue'
  import Row_Flex from './components/Row_Flex.vue'
  import InputA from './components/input_autocomplete.vue'
  export default {
    data () {
      return {
        value2: '',
        data2: [],
        model13: '',
        options1: [],
        list: ['Alabama', 'Alaska', 'Arizona', 'Arkansas', 'California', 'Colorado', ]
      }
    },
    components: {
      Date,
      ChangeClass,
      Row_Flex,
      InputA,
      ESelect
    },
    mounted(){
      this.value2 = '中文';
      this.model13 = 'a';
    },
    methods: {
      handleSearch2 (value) {
        this.data2 = [
          {id: 1, name: 'xxx'},
          {id: 2, name: 'yyy'},
          {id: 3, name: 'www'},
        ]
      },
      handleSelect(e){
        console.log(e);
      },
      remoteMethod1(query){
        if (query !== '') {
          setTimeout(() => {
            const list = this.list.map(item => {
              return {
                value: item,
                label: item
              };
            });
            this.options1 = list.filter(item => item.label.toLowerCase().indexOf(query.toLowerCase()) > -1);
          }, 200);
        } else {
          this.options1 = [];
        }
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
  .ivu-tabs{
    overflow: visible!important;
  }
</style>