<template>
  <div>
    <Tabs :animated="false">
      <TabPane label="来源排名">
        <v-header></v-header>
        <div class="conents">

        </div>
      </TabPane>
      <TabPane label="销量对比">销量对比</TabPane>
      <TabPane label="品类排名">品类排名</TabPane>
      <TabPane label="单款排名">单款排名</TabPane>
      <TabPane label="客户排名">客户排名</TabPane>
    </Tabs>

  </div>
</template>
<script>
import vHeader from './v-header.vue';

export default {
    components: {
        vHeader
    },
    data () {
        return {
            v_tabs: ['来源排名', '销量对比', '品类排名', '单款排名', '客户排名']

        };
    }
};
</script>



<style lang="less" scoped>
.conents {
  height: 500px;
  width: 100%;
  margin-top: 5px;
}
</style>

<style lang="less">
.ivu-tabs-bar {
  margin-bottom: 5px;
}
</style>