<style scoped>
</style>
<template>
  <div>
    <Row>
      <i-col span="24">
        <span class="expand-key">
          请求数据:
        </span>
        <span class="expand-value">
          {{ row.data }}
        </span>
      </i-col>
    </Row>
  </div>
</template>
<script>
export default {
    props: {
        row: Object
    }
};
</script>
