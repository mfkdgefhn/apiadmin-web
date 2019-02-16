<template>
  <div>
    <row :gutter="10"
         class="row-hear">
      <Card style="min-width:600px;">
        <div>

          <span>来源筛选：</span>
          <i-select :model.sync="model1"
                    clearable
                    style="width:200px"
                    @on-change="setSotype">
            <i-option v-for="item in SOTYPE"
                      :value="item.value"
                      :key="item.value">
              {{ item.label }}
            </i-option>
          </i-select>
          <span>日期筛选：</span>
          <i-select :model.sync="model2"
                    clearable
                    style="width:200px"
                    @on-change="setSotype">
            <i-option v-for="item in SOTYPE"
                      :value="item.value"
                      :key="item.value">
              {{ item.label }}
            </i-option>
          </i-select>
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
            model1: '',
            model2: '',
            loading: false
        };
    },
    methods: {
        toLoading () {
            // eslint-disable-next-line no-console
            console.log(this.model1);
        },
        setSotype (data) {
            this.model1 = data;
        }
    }
};
</script>
