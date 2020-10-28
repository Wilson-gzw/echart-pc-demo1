<!--  -->
<template>
  <div class="top-sales">
    <common-card title="累计销售额" value="￥ 32,039,165">
      <!--中间部分  -->
      <template>
        <div class="compare">
          <div class="compare-top">
            <span>日同比</span>
            <span class="emphasis">7.33%</span>
            <div class="increase" />
          </div>
          <div class="compare-bottom">
            <span>月同比</span>
            <span class="emphasis">7.33%</span>
            <div class="decrease" />
          </div>
        </div>
      </template>
      <!-- 底部部分 -->
      <template v-slot:footer>
        <span>昨日销售额</span>
        <span class="money">￥ 30,000,000</span>
      </template>
    </common-card>
  </div>
</template>

<script>
// 这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
// 例如：import 《组件名称》 from '《组件路径》';
import CommonCardMixins from '@/mixins/common-card-mixins.js'

export default {
  name: 'TopSales',
  mixins: [CommonCardMixins],
  data () {
    // 这里存放数据
    return {}
  },
  // 监听属性 类似于data概念
  computed: {},
  // 监控data中的数据变化
  watch: {},
  // 方法集合
  methods: {}
}
</script>
<style lang="scss" scoped>
//@import url(); 引入公共css类

.money {
  margin-left: 5px;
  color: #333;
  font-weight: 700;
}
.compare {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .compare-top {
    display: flex;
    flex-direction: row;
    align-items: center;
    flex: 1;
  }
  .compare-bottom {
    display: flex;
    flex-direction: row;
    align-items: center;
    flex: 1;
  }
}
</style>

<style>
.emphasis {
  margin-left: 5px;
  color: #333;
  font-weight: 700;
}

.increase {
  width: 0;
  height: 0;
  border-width: 3px;
  border-color: transparent transparent red transparent;
  border-style: solid;
  margin: 0 0 5px 5px;

}

.decrease {
  width: 0;
  height: 0;
  border-width: 3px;
  border-color: green transparent transparent transparent;
  border-style: solid;
  margin: 6px 0 0 5px;

}
</style>
