<!--
 * @LastEditTime: 2024-11-11 16:27:24
 * @Description: 
-->
<template>
  <div class="tool-box">
    <Button
      v-show="isViewHandleData"
      type="success"
      @click="handleData"
      class="data-btn"
      >操作数据</Button
    >
    <Poptip width="170" placement="bottom-end">
      <Button icon="ios-git-merge" type="info" @click="handleRang">测距</Button>
      <div class="api" slot="content">
        <div class="rang-tip">
          使用提示：<span class="rang-tip-text">右键结束</span>
        </div>
      </div>
    </Poptip>
  </div>
</template>
<script>
export default {
  props: {
    rangChecked: {
      default: "null"
    }
  },
  data() {
    return {
      isViewHandleData: true
    };
  },
  mounted() {
    this.$bus.$on("YhFileOk", value => {
      this.isViewHandleData = true;
    });
  },
  methods: {
    handleRang() {
      this.$bus.$emit("rangFun", {
        rangChecked: "ready"
      });
    },
    handleData() {
      this.$bus.$emit("handleData", {
        operationSign: 0
      });
    }
  }
};
</script>
<style>
.tool-box {
  width: 180px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: flex-end;
}
.data-btn {
  margin-right: 12px;
}
.rang-tip {
  width: 100%;
  color: red;
}
.rang-tip-text {
  font-weight: bold;
}
</style>
