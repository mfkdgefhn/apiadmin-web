<template>
  <div>
    <row :gutter="10">
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
          <!-- 这是一个文件 -->
        </Card>
      </i-col>
    </row>
  </div>
</template>

<script>
export default {
    data () {
        return {

        };
    },
    props: {
        conent: {
            type: String
        }
    }
};
</script>