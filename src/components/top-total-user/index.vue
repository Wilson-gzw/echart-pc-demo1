<!--  -->
<template>
  <div class="top-total-user">
    <common-card title="累计用户数" value="1，087,503">
      <!--中间部分  -->
      <template>
        <div id="total-user-chart" :style="{ width: '100%', height: '100%' }" />
      </template>
      <!-- 底部部分 -->
      <template v-slot:footer>
        <div class="footer-container">
          <span>日同比</span>
          <span class="emphasis">8.33%</span>
          <div class="increase" />
          <span style="margin-left: 10px;">月同比</span>
          <span class="emphasis">35.91%</span>
          <div class="decrease" />
        </div>
      </template>
    </common-card>
  </div>
</template>

<script>
// 这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
// 例如：import 《组件名称》 from '《组件路径》';
import CommonCardMixins from '@/mixins/common-card-mixins.js'

export default {
  name: 'TopTotalUser',
  mixins: [CommonCardMixins],
  data () {
    // 这里存放数据
    return {}
  },
  mounted () {
    const chartDom = document.getElementById('total-user-chart')
    const chart = this.$echarts.init(chartDom)
    chart.setOption({
      xAxis: {
        type: 'value',
        show: false
      },
      yAxis: {
        type: 'category',
        show: false
      },
      series: [
        {
          type: 'bar',
          stack: '总量',
          data: [140],
          barWidth: 10,
          itemStyle: { color: '#45c946' }
        },
        {
          type: 'bar',
          stack: '总量',
          data: [250],
          itemStyle: { color: '#eee' }
        },
        {
          type: 'custom',
          stack: '总量',
          data: [140],
          renderItem: (params, api) => {
            const value = api.value(0)
            const endPoint = api.coord([value, 0])
            return {
              type: 'group',
              position: endPoint,
              children: [{
                type: 'path',
                shape: { d: 'M514.525867 67.529387L3.413333 953.53856l1017.173334 2.92864L514.525867 67.529387z', x: -5, y: 8, width: 10, height: 10 },
                style: { fill: '#45c946' },
                layout: 'cover'
              }, {
                type: 'path',
                shape: { d: 'M514.525867 956.474027L3.413333 70.46144l1017.173334-2.932053-506.0608 888.94464z', x: -5, y: -19, width: 10, height: 10 },
                style: { fill: '#45c946' },
                layout: 'cover'
              }]

            }
          }
        }
      ],
      grid: {
        top: 0,
        left: 0,
        right: 0,
        bottom: 0
      }
    })
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
.footer-container {
  display: flex;
  flex-direction: row;
  align-items: center;
}
</style>
