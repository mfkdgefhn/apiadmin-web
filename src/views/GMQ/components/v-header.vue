<template>
  <div>
    <row :gutter="10"
         class="row-hear">
      <Card style="min-width:600px;">
        <div>
          <!-- 来源 -->
          <span class="jiange">来源筛选：</span>
          <i-select :model.sync="model1"
                    clearable
                    ref="sotype"
                    style="width:90px"
                    @on-change="setSotype"
                    placeholder="默认本厂">
            <i-option v-for="item in SOTYPE"
                      :value="item.value"
                      :key="item.value">
              {{ item.label }}
            </i-option>
          </i-select>
          <!-- 品类 -->
          <span class="jiange">品类筛选：</span>
          <i-select :model.sync="model1"
                    clearable
                    ref="sotype"
                    style="width:90px"
                    @on-change="setSotype"
                    placeholder="默认本厂">
            <i-option v-for="item in SOTYPE"
                      :value="item.value"
                      :key="item.value">
              {{ item.label }}
            </i-option>
          </i-select>
          <!-- 客户属性 -->
          <span class="jiange">客户属性：</span>
          <i-select :model.sync="model1"
                    clearable
                    ref="sotype"
                    style="width:90px"
                    @on-change="setSotype"
                    placeholder="默认本厂">
            <i-option v-for="item in SOTYPE"
                      :value="item.value"
                      :key="item.value">
              {{ item.label }}
            </i-option>
          </i-select>
          <!-- 客户 -->
          <span class="jiange">客户：</span>
          <i-select :model.sync="model1"
                    clearable
                    ref="sotype"
                    style="width:90px"
                    @on-change="setSotype"
                    placeholder="默认本厂">
            <i-option v-for="item in SOTYPE"
                      :value="item.value"
                      :key="item.value">
              {{ item.label }}
            </i-option>
          </i-select>
          <!-- 日期 -->
          <i-switch class="jiange"
                    size="large"
                    v-model="showDate"
                    @on-change="setShowDate">
            <span slot="open">截止</span>
            <span slot="close">区间</span>
          </i-switch>
          <DatePicker v-if="showDate"
                      class="jiange"
                      type="date"
                      format="yyyyMMdd"
                      :value="vJzdate"
                      :options="options1"
                      clearable
                      placeholder="请输入截止日期"
                      style="width: 130px"
                      @on-change="setJzTime">
          </DatePicker>
          <DatePicker v-else
                      class="jiange"
                      type="daterange"
                      format="yyyyMMdd"
                      :value="vQJdate"
                      :options="options2"
                      clearable
                      placeholder="请输入区间日期"
                      style="width:180px"
                      @on-change="setQjTime">
          </DatePicker>

          <!-- <span class="jiange">模糊搜索：</span> -->
          <Input class="jiange"
                 v-model="value14"
                 placeholder="模糊搜索款号"
                 clearable
                 style="width: 100px" />

          <!-- 搜索 -->
          <Button class="jiange"
                  type="primary"
                  shape="circle"
                  icon="ios-search"
                  :loading="loading"
                  @click="toLoading">
            搜索
          </Button>
        </div>
      </Card>
    </row>
  </div>
</template>

<script>
export default {
    data () {
        return {
            SOTYPE: [
                { value: '1', label: '本厂' },
                { value: '2', label: '外购' },
                { value: '1,2', label: '全部' }
            ],
            model1: '1',
            value14: '',
            loading: false,
            vJzdate: '',
            vQJdate: '',
            showDate: true,
            options1: {
                shortcuts: [
                    {
                        text: '昨天',
                        value () {
                            const date = new Date();
                            date.setTime(date.getTime() - 3600 * 1000 * 24);

                            return date;
                        },
                        onClick: (picker) => {
                            this.$Message.info('点击昨天');
                        }
                    },
                    {
                        text: '前天',
                        value () {
                            const date = new Date();
                            date.setTime(date.getTime() - 3600 * 1000 * 24 * 2);
                            return date;
                        },
                        onClick: (picker) => {
                            this.$Message.info('点击前天');
                        }
                    },
                    {
                        text: '一周前',
                        value () {
                            const date = new Date();
                            date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
                            return date;
                        },
                        onClick: (picker) => {
                            this.$Message.info('点击一周前');
                        }
                    }
                ]
            },
            options2: {
                shortcuts: [
                    {
                        text: '1周',
                        value () {
                            const end = new Date();
                            end.setTime(end.getTime() - 3600 * 1000 * 24);
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
                            return [start, end];
                        }
                    },
                    {
                        text: '1月',
                        value () {
                            const end = new Date();
                            end.setTime(end.getTime() - 3600 * 1000 * 24);
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
                            return [start, end];
                        }
                    },
                    {
                        text: '3月',
                        value () {
                            const end = new Date();
                            end.setTime(end.getTime() - 3600 * 1000 * 24);
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
                            return [start, end];
                        }
                    }
                ]
            }
        };
    },
    created () {
        this.setTime();
    },
    methods: {
        toLoading () {
            if (this.showDate) {
                // eslint-disable-next-line no-console
                console.log(this.vJzdate);
            } else {
                // eslint-disable-next-line no-console
                console.log(this.vQJdate);
            }
        },
        setSotype (data) {
            this.model1 = data;
            // eslint-disable-next-line no-console
            console.log(data);
        },
        setShowDate () {
            // eslint-disable-next-line no-console
            console.log(this.showDate);
            // this.switchValue = !this.switchValue;
        },
        setTime () {
            this.vJzdate = this.$moment().subtract(1, 'days').format('YYYYMMDD');
            this.vQJdate = this.setQjvalue;
        },
        setJzTime (data) {
            // eslint-disable-next-line no-console
            console.log(data);
            this.vJzdate = data;
        },
        setQjTime (data) {
            // eslint-disable-next-line no-console
            console.log(data);
            this.vQJdate = data;
        }
    },
    computed: {
        setQjvalue () {
            // const end = new Date();
            // const start = new Date();
            // start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
            // return [start, end];
            const start = this.$moment().subtract(7, 'days').format('YYYYMMDD');
            const end = this.$moment().subtract(1, 'days').format('YYYYMMDD');
            return [start, end];
        }
    }
};
</script>

<style scoped>
.jiange {
  margin: 10px;
}
</style>
