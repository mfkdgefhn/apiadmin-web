<template>
  <div class="bi">
    <!-- 头部 -->
    <row :gutter="10"
         class="row-hear">
      <Card style="min-width:600px;">
        <div>
          <span>截止日期：</span>
          <DatePicker :value="vJzdate"
                      format="yyyyMMdd"
                      type="date"
                      placeholder="请输入截止日期"
                      style="width: 120px"
                      @on-change="setJzdate">
          </DatePicker>
          <span>产品年份：</span>
          <DatePicker type="year"
                      :value="vYear"
                      placeholder="请输入款号年份"
                      style="width: 120px"
                      @on-change="setYear">
          </DatePicker>
          <Button type="primary"
                  shape="circle"
                  icon="ios-search"
                  :loading="loading"
                  @click="toLoading">
            搜索
          </Button>
        </div>
      </Card>
    </row>

    <!-- 中部 -->
    <row :gutter="10">
      <!-- 春 -->
      <i-col :xs="24"
             :sm="24"
             :md="12">
        <Card>
          <img v-if="data37.length>0"
               :src=data37[0].KH>
          <img v-else
               src="http://10.10.1.32:8018/Images/sku/spring.jpg"
               @click="modal11 = true">

          <Table class="nxfx-1"
                 border
                 :columns="columns1"
                 :data="data37">
          </Table>
        </Card>
      </i-col>
      <!-- 夏 -->
      <i-col :xs="24"
             :sm="24"
             :md="12">
        <Card>
          <img v-if="data38.length>0"
               :src=data38[0].KH>
          <img v-else
               src="http://10.10.1.32:8018/Images/sku/summer.jpg">
          <Table class="nxfx-1"
                 border
                 :columns="columns1"
                 :data="data38">
          </Table>
        </Card>
      </i-col>
    </row>
    <row :gutter="10">
      <!-- 秋 -->
      <i-col :xs="24"
             :sm="24"
             :md="12">
        <Card>
          <img v-if="data39.length>0"
               :src=data39[0].KH>
          <img v-else
               src="http://10.10.1.32:8018/Images/sku/autumn.jpg">
          <Table class="nxfx-1"
                 border
                 :columns="columns1"
                 :data="data39">
          </Table>
        </Card>
      </i-col>
      <!-- 冬 -->
      <i-col :xs="24"
             :sm="24"
             :md="12">
        <Card>
          <img v-if="data40.length>0"
               :src=data40[0].KH>
          <img v-else
               src="http://10.10.1.32:8018/Images/sku/winter.jpg">
          <Table class="nxfx-1"
                 border
                 :columns="columns1"
                 :data="data40">
          </Table>
        </Card>
      </i-col>
    </row>
    <!-- 弹出层 -->
    <Modal v-model="modal11"
           footer-hide
           scrollable>
      <!-- fullscreen -->
      <!-- title="Fullscreen Modal" -->
      <bi2></bi2>
    </Modal>

  </div>
</template>

<script>
import axios from 'axios';
import bi2 from './components/bi2.vue';

export default {
    name: 'bi_index',
    components: {
        bi2
    },
    data () {
        return {
            hash: '5c4d6dc93a515',
            modal11: false,
            vYear: '',
            vJzdate: '',
            loading: false,
            columns1: [
                {
                    title: '季节',
                    key: 'JI'
                }, {
                    title: '发货量',
                    key: 'FHL'
                },
                {
                    title: '补单量',
                    key: 'BH'
                },
                {
                    title: '补单%',
                    key: 'BDL'
                },
                {
                    title: '款数',
                    key: 'KS'
                }
            ],
            data1: [],
            data37: [],
            data38: [],
            data39: [],
            data40: []
        };
    },
    created () {
        this.getTime();
    },
    methods: {
        toLoading () {
            let vm = this;
            let vDate = '';
            let xuanran = this.xuanran;
            // 加载
            this.loading = !this.loading;
            let url = 'http://www.api.com/bi/5c527fc326ead?vYear=';
            url = url + vm.vYear + '&vJzdate=' + vm.vJzdate + '&hash=' + vm.hash;
            vm.data1 = [];
            axios.get(url).then(function (response) {
                // 获取数据
                vDate = response.data.data;
                vm.data1 = vDate;
                // 渲染数据
                xuanran(vDate);
                // 去掉加载
                vm.loading = !vm.loading;
            }).catch(function (error) {
                // 抛错
                // eslint-disable-next-line no-console
                console.log(error);
                vm.$Message.error('请求错误，请看console');
                vm.loading = !vm.loading;
            });
        },
        setJzdate (date) {
            this.vJzdate = date;
        },
        setYear (Year) {
            this.vYear = Year;
        },
        getTime () {
            // 昨天的日期格式
            this.vYear = this.$moment().subtract(1, 'days').format('YYYY');
            this.vJzdate = this.$moment().subtract(1, 'days').format('YYYYMMDD');
        },
        xuanran (vDate) {
            let xuanran41 = this.xuanran41;
            xuanran41(vDate);
        },
        xuanran41 (data) {
            this.data37 = [];
            this.data38 = [];
            this.data39 = [];
            this.data40 = [];
            if (data) {
                for (let index = 0; index < data.length; index++) {
                    if (data[index].SEASON_ID === '37') {
                        this.data37.push(data[index]);
                    } else if (data[index].SEASON_ID === '38') {
                        this.data38.push(data[index]);
                    } else if (data[index].SEASON_ID === '39') {
                        this.data39.push(data[index]);
                    } else if (data[index].SEASON_ID === '40') {
                        this.data40.push(data[index]);
                    }
                }
            }
        }
    },
    computed: {
        getDate (index) {
            let vm = this.data1;
            let data = [];
            for (let j = 0; j < this.data1.length; j++) {
                if (vm[j].SEASON_ID === index) {
                    data.push(vm[j]);
                }
            }
            return data;
        }
    }
};
</script>

<style lang="less" scoped>
.ivu-date-picker {
  margin-right: 20px;
}
.row-hear {
  margin-bottom: 10px;
}
.ivu-col {
  text-align: center;
  margin-bottom: 10px;
}
img {
  width: 40%;
}
</style>
