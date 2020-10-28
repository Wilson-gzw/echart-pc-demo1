<!--  -->
<template>
  <div class="top-order">
    <common-card title="累计订单量" value="2,157,420">
      <!--中间部分  -->
      <template>
        <div
          id="total-order-chart"
          :style="{ width: '100%', height: '100%' }"
        />
      </template>
      <!-- 底部部分 -->
      <template v-slot:footer>
        <span>昨日订单量</span>
        <span class="money">2,000,000</span>
      </template>
    </common-card>
  </div>
</template>

<script>
// 这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
// 例如：import 《组件名称》 from '《组件路径》';
import CommonCardMixins from '@/mixins/common-card-mixins.js'

export default {
  name: 'TopOrder',
  mixins: [CommonCardMixins],
  data () {
    // 这里存放数据
    return {}
  },
  // 监听属性 类似于data概念
  computed: {},
  // 监控data中的数据变化
  watch: {},
  mounted () {
    const chartDom = document.getElementById('total-order-chart')
    const chart = this.$echarts.init(chartDom)
    chart.setOption({
      xAxis: {
        type: 'category',
        show: false,
        boundaryGap: false
      },
      yAxis: {
        show: false
      },
      series: [
        {
          type: 'line',
          data: [
            628,
            432,
            220,
            534,
            798,
            430,
            220,
            320,
            532,
            320,
            834,
            698,
            530,
            228,
            620
          ],
          areaStyle: {
            color: 'purple'
          },
          lineStyle: { width: 0 },
          itemStyle: { opacity: 0 },
          smooth: true
        }
      ],
      grid: {
        top: 0,
        bottom: 0,
        left: 0,
        right: 0
      }
    })
  },
  // 方法集合
  methods: {}
}
</script>
<style lang="scss" scoped>
//@import url(); 引入公共css类
.compare {
  height: 100%;
}
</style>
