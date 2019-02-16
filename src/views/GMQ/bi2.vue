

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
    <row :gutter="16">
      <i-col v-for="i in img_data"
             :key=i.id
             :xs="24"
             :sm="24"
             :md="12">
        <Card>
          <img :src=i.img>
          <!-- <img :src='http://10.10.1.32:8018/Images/sku/'+i.img+'.jpg'> -->
          
          <Table class="nxfx-1"
                 border
                 :columns="columns1"
                 :data="data1">
          </Table>
        </Card>
      </i-col>
    </row>

  </div>
</template>

<script>
import Axios from 'axios';

export default {
    name: 'bi_index',
    components: {
    },
    data () {
        return {
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
            data1: [
                {
                    JI: '春季本厂',
                    FHL: '605790',
                    BH: '127986',
                    BDL: '21.13%',
                    KS: '77'
                }, {
                    JI: '春季外购',
                    FHL: '200040',
                    BH: '3540',
                    BDL: '1.77%',
                    KS: '23'
                }
            ],
            // (i['补货'] / i['发货量'] * 100).toFixed(2)
            img_data: [
                { id: 1, img: 'spring' },
                { id: 2, img: 'summer' },
                { id: 3, img: 'autumn' },
                { id: 4, img: 'winter' }
            ]
        };
    },
    created () {
        this.getTime();
    },
    methods: {
        toLoading () {
            let vm = this;
            let xuanran = this.xuanran;
            let vDate = '';
            this.loading = !this.loading;
            let url = 'http://www.api.com/bi/5c527fc326ead?vYear=';
            url = url + vm.vYear + '&vJzdate=' + vm.vJzdate;
            // eslint-disable-next-line no-console
            console.log(url);
            // eslint-disable-next-line no-console
            // console.log(vm.data1);
            vm.data1 = [];
            Axios.get(url).then(function (response) {
                vDate = response.data.data;
                // eslint-disable-next-line no-console
                console.log(vDate);
                vm.data1 = vDate;
                xuanran(vDate);
                vm.loading = !vm.loading;
            }).catch(function (error) {
                // eslint-disable-next-line no-console
                console.log(error);
                vm.$Message.error('请求错误，请看console');
                vm.loading = !vm.loading;
            });
        },
        setJzdate (date) {
            // eslint-disable-next-line no-console
            console.log(date);
            this.vJzdate = date;
        },
        setYear (Year) {
            // eslint-disable-next-line no-console
            console.log(Year);
            this.vYear = Year;
        },
        getTime () {
            // 昨天的日期格式
            this.vYear = this.$moment().subtract(1, 'days').format('YYYY');
            this.vJzdate = this.$moment().subtract(1, 'days').format('YYYYMMDD');
        },
        xuanran (data) {
            // eslint-disable-next-line no-console
            console.log(1111);
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
  // min-width: 450px;
}
img {
  width: 40%;
}
</style>
