<template>
  <div>
    <row :gutter="10"
         class="row-hear">
      <Card style="min-width:600px;">
        <div>
          <!-- 来源 -->
          <div class="jiange"
               v-if="isSotype">
            <span>来源：</span>
            <i-select :model.sync="model1"
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
          </div>

          <!-- 品类 -->
          <div class="jiange"
               v-if="isCategory">
            <span>品类：</span>
            <i-select :model.sync="model2"
                      clearable
                      multiple
                      style="width:110px"
                      @on-change="setSotype"
                      placeholder="默认全部">
              <i-option v-for="item in model2"
                        :value="item.value"
                        :key="item.value">
                {{ item.label }}
              </i-option>
            </i-select>
          </div>

          <!-- 客户属性 -->
          <div class="jiange"
               v-if="isCustomer">
            <span>客户属性：</span>
            <i-select :model.sync="model3"
                      style="width:90px"
                      @on-change="setSotype"
                      placeholder="默认全国">
              <i-option v-for="item in model3"
                        :value="item.value"
                        :key="item.value">
                {{ item.label }}
              </i-option>
            </i-select>
          </div>

          <!-- 客户 -->
          <div class="jiange"
               v-if="isCustomer1">
            <span>客户：</span>
            <i-select :model.sync="model4"
                      style="width:90px"
                      @on-change="setSotype"
                      placeholder="默认全部">
              <i-option v-for="item in model4"
                        :value="item.value"
                        :key="item.value">
                {{ item.label }}
              </i-option>
            </i-select>
          </div>

          <!-- 日期 -->
          <div class="jiange"
               v-if="isData">
            <i-switch size="large"
                      v-model="showDate">
              <span slot="open">截止</span>
              <span slot="close">区间</span>
            </i-switch>
            <DatePicker v-if="showDate"
                        type="date"
                        format="yyyyMMdd"
                        :value="vJzdate"
                        :options="options1"
                        placeholder="请输入截止日期"
                        style="width: 130px"
                        @on-change="setJzTime">
            </DatePicker>
            <DatePicker v-else
                        type="daterange"
                        format="yyyyMMdd"
                        :value="vQJdate"
                        :options="options2"
                        placeholder="请输入区间日期"
                        style="width:180px"
                        @on-change="setQjTime">
            </DatePicker>
          </div>

          <!-- 排序 -->
          <div class="jiange"
               v-if="isOrder">
            <span>排序：</span>
            <i-select :model.sync="model5"
                      style="width:90px"
                      placeholder="默认销量">
              <i-option v-for="item in model5"
                        :value="item.value"
                        :key="item.value">
                {{ item.label }}
              </i-option>
            </i-select>
          </div>

          <!-- <span class="jiange">模糊搜索：</span> -->
          <div class="jiange"
               v-if="isSelect">
            <Input v-model="value14"
                   placeholder="模糊搜索款号"
                   clearable
                   style="width: 100px" />
          </div>

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
    props: {
        isSotype: {
            type: Boolean,
            default: false
        },
        isCategory: {
            type: Boolean,
            default: false
        },
        isData: {
            type: Boolean,
            default: false
        },
        isSelect: {
            type: Boolean,
            default: false
        },
        isCustomer: {
            type: Boolean,
            default: false
        },
        isCustomer1: {
            type: Boolean,
            default: false
        },
        isOrder: {
            type: Boolean,
            default: false
        }
    },
    data () {
        return {
            SOTYPE: [
                { value: '1', label: '本厂' },
                { value: '2', label: '外购' },
                { value: '1,2', label: '全部' }
            ],
            model1: '1',
            model2: [
                { value: '1', label: '凉鞋' },
                { value: '2', label: '浅口鞋' },
                { value: '3', label: '运动鞋' },
                { value: '4', label: '板鞋' },
                { value: '5', label: '厚棉鞋' },
                { value: '6', label: '雪地棉鞋' },
                { value: '7', label: '拖鞋' },
                { value: '8', label: '中口鞋' },
                { value: '9', label: '棉鞋' },
                { value: '10', label: '深口鞋' },
                { value: '11', label: '空鞋' },
                { value: '12', label: '薄棉鞋' }
            ],
            model3: [
                { value: '1', label: '全国' },
                { value: '2', label: '直管经销商' },
                { value: '3', label: '经销商' }
            ],
            model4: [],
            model5: [
                { value: '1', label: '按销量' },
                { value: '2', label: '按发货' },
                { value: '3', label: '按售馨' }
            ],
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

<style>
.jiange {
  display: inline-block;
  margin: 5px 5px;
}
</style>
