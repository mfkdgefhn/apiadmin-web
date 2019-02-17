<template>
  <div>
    <Tabs :animated="false">
      <TabPane v-for="item in v_tabs"
               :key="item.value"
               :label="item.label">
        <v-header :isCategory="item.isCategory"
                  :isCustomer="item.isCustomer"
                  :isCustomer1="item.isCustomer1"
                  :isData="item.isData"
                  :isOrder="item.isOrder"
                  :isSelect="item.isSelect"
                  :isSotype="item.isSotype"></v-header>
        <!-- <div class="conents">
          
        </div> -->
        <v-conent class="conents"
                  :conent="item.label"></v-conent>
      </TabPane>
    </Tabs>
  </div>
</template>
<script>
import vHeader from './v-header.vue';
import vConent from './v-conent.vue';

export default {
    components: {
        vHeader,
        vConent
    },
    methods: {
    },
    data () {
        return {
            v_tabs: [
                {
                    value: '0',
                    label: '来源排名',
                    isSotype: true,
                    isData: true,
                    isSelect: true,
                    isOrder: true,
                    isCategory: false,
                    isCustomer: false,
                    isCustomer1: false
                }, {
                    value: '1',
                    label: '销量对比',
                    isData: true,
                    isSelect: true,
                    isSotype: false,
                    isOrder: false,
                    isCategory: false,
                    isCustomer: false,
                    isCustomer1: false
                }, {
                    value: '2',
                    label: '品类排名',
                    isCategory: true,
                    isData: true,
                    isSelect: true,
                    isOrder: true,
                    isSotype: false,
                    isCustomer: false,
                    isCustomer1: false
                }, {
                    value: '3',
                    label: '单款排名',
                    isCustomer: true,
                    isCustomer1: true,
                    isData: true,
                    isSelect: true,
                    isOrder: true,
                    isSotype: false,
                    isCategory: false
                }, {
                    value: '4',
                    label: '客户排名',
                    isCustomer: true,
                    isCustomer1: true,
                    isData: true,
                    isSelect: true,
                    isOrder: true,
                    isSotype: false,
                    isCategory: false
                }]

        };
    }
};
</script>



<style lang="less" scoped>
.conents {
  height: 100%;
  min-height: 300px;
  width: 100%;
  background: rgb(148, 185, 255);
  margin-top: 5px;
}
</style>

<style lang="less">
.ivu-tabs-bar {
  margin-bottom: 5px;
}
</style>