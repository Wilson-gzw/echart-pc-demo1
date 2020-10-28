<!--  -->
<template>
  <div class="top-user">
    <common-card title="今日交易用户数" value="81,014">
      <!--中间部分  -->
      <template>
        <div
          id="today-user-chart"
          :style="{ width: '100%', height: '100%' }"
        />
      </template>
      <!-- 底部部分 -->
      <template v-slot:footer>
        <span>退货款</span>
        <span class="money">5.14%</span>
      </template>
    </common-card>
  </div>
</template>

<script>
// 这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
// 例如：import 《组件名称》 from '《组件路径》';
import CommonCardMixins from '@/mixins/common-card-mixins.js'

export default {
  name: 'TopUser',
  mixins: [CommonCardMixins],
  data () {
    // 这里存放数据
    return {}
  },
  mounted () {
    const chartDom = document.getElementById('today-user-chart')
    const chart = this.$echarts.init(chartDom)
    chart.setOption({
      color: ['#3398DB'],

      xAxis: {
        type: 'category',
        data: ['01:00', '02:00', '03:00', '04:00', '05:00', '06:00', '07:00', '08:00', '09:00', '10:00', '11:00', '12:00', '13:00'],
        show: false
      },
      yAxis: {
        show: false
      },
      series: [{
        type: 'bar',
        data: [410, 82, 200, 334, 390, 330, 220, 150, 82, 200, 134, 290, 330, 150],
        barWidth: '60%'
      }],
      grid: {
        top: 0,
        left: 0,
        right: 0,
        bottom: 0
      }
    })
  }
}
</script>
<style lang="scss" scoped>
//@import url(); 引入公共css类
</style>
