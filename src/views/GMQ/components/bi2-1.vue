<template>
  <div>
    <Tabs :animated="false">
      <TabPane label="来源排名">
        <v-header isSotype
                  isData
                  isSelect
                  isOrder></v-header>
        <div class="conents">
          来源排名
        </div>
        <v-conent></v-conent>
      </TabPane>
      <TabPane label="销量对比">
        <v-header isData
                  isSelect></v-header>
        <div class="conents">
          销量对比
        </div>
      </TabPane>
      <TabPane label="品类排名">
        <v-header isCategory
                  isData
                  isSelect
                  isOrder></v-header>
        <div class="conents">
          品类排名
        </div>
      </TabPane>
      <TabPane label="单款排名">
        <v-header isCustomer
                  isCustomer1
                  isData
                  isSelect
                  isOrder></v-header>
        <div class="conents">
          单款排名
        </div>
      </TabPane>
      <TabPane label="客户排名">
        <v-header isCustomer
                  isCustomer1
                  isData
                  isSelect
                  isOrder></v-header>
        <div class="conents">
          客户排名
        </div>
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
    data () {
        return {
            v_tabs: [
                {
                    value: '1',
                    label: '来源排名',
                    attrs: ['isSotype',
                        'isData',
                        'isSelect',
                        'isOrder']
                }, {
                    value: '2',
                    label: '销量对比',
                    attrs: ['isData',
                        'isSelect']
                }, {
                    value: '3',
                    label: '品类排名',
                    attrs: ['isCategory',
                        'isData',
                        'isSelect',
                        'isOrder']
                }, {
                    value: '4',
                    label: '单款排名',
                    attrs: ['isCustomer',
                        'isCustomer1',
                        'isData',
                        'isSelect',
                        'isOrder']
                }, {
                    value: '5',
                    label: '客户排名',
                    attrs: ['isCustomer',
                        'isCustomer1',
                        'isData',
                        'isSelect',
                        'isOrder']
                }]

        };
    }
};
</script>



<style lang="less" scoped>
.conents {
  height: 300px;
  width: 100%;
  margin-top: 5px;
}
</style>

<style lang="less">
.ivu-tabs-bar {
  margin-bottom: 5px;
}
</style>