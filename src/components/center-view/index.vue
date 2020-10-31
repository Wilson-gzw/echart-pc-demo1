<!--  -->
<template>
  <div class="center-view">
    <el-card shadow="hover" :body-style="{ padding: '0 0 20px 0' }">
      <template v-slot:header>
        <div class="header-wrapper">
          <div class="menu">
            <el-menu
              mode="horizontal"
              :default-active="activeIndex"
              @select="handleSelect"
            >
              <el-menu-item index="1">销售额</el-menu-item>
              <el-menu-item index="2">访问量</el-menu-item>
            </el-menu>
          </div>
          <div class="wrapper-right">
            <el-radio-group v-model="radioSelect" size="small">
              <el-radio-button label="今日" />
              <el-radio-button label="本周" />
              <el-radio-button label="本月" />
              <el-radio-button label="今年" />
            </el-radio-group>
            <el-date-picker
              type="daterange"
              style="margin-left: 20px;"
              unlink-panels
              v-model="date"
              start-placeholder="开始日期"
              range-separator="至"
              end-placeholder="结束日期"
              :picker-options="pickerOptions"
              size="small"
            ></el-date-picker>
          </div>
        </div>
      </template>
      <template>
        <div class="main-chart-wrapper">
          <v-chart  class="chart" :options="chartOptions"></v-chart>
          <div class="main-list">
            <div class="list-title">排行榜</div>
            <div class="list-item" v-for="item in rankData" :key="item.no">
              <div
                class="list-item-no"
                :class="{ 'top-no': Number(item.no) <= 3 }"
              >
                {{ item.no }}
              </div>
              <div class="list-item-name">{{ item.name }}</div>
              <div class="list-item-money">{{ item.money }}</div>
            </div>
          </div>
        </div>
      </template>
    </el-card>
  </div>
</template>

<script>
// 这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
// 例如：import 《组件名称》 from '《组件路径》';

export default {
  name: 'CenterView',
  components: {},
  data () {
    // 这里存放数据
    return {
      activeIndex: '1',
      radioSelect: '今日',
      date: null,
      pickerOptions: {
        shortcuts: [
          {
            text: '最近一周',
            onClick (picker) {
              const start = new Date()
              const end = new Date()
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 7)
              picker.$emit('pick', [start, end])
            }
          },
          {
            text: '最近一个月',
            onClick (picker) {
              const start = new Date()
              const end = new Date()
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 30)
              picker.$emit('pick', [start, end])
            }
          },
          {
            text: '最近三个月',
            onClick (picker) {
              const start = new Date()
              const end = new Date()
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 90)
              picker.$emit('pick', [start, end])
            }
          }
        ]
      },
      chartOptions: {
        title: {
          text: '年度销售额',
          textStyle: {
            color: '#333',
            fontSize: 12
          },
          left: 25,
          top: 20
        },
        xAxis: {
          type: 'category',
          data: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月'],
          axisTick: {
            alignWithLabel: true,
            lineStyle: { color: '#999 ' }
          },
          axisLine: {
            lineStyle: { color: '#999' }
          },
          axisLabel: {
            color: '#333'
          }
        },
        yAxis: {
          axisLine: {
            show: false,
            axisTick: { show: false },
            splitLine: {
              lineStyle: { type: 'dotted', color: '#eee' }
            }
          }
        },
        series: [{
          type: 'bar',
          barWidth: '35%',
          data: [200, 250, 300, 350, 300, 250, 200, 250, 300, 350, 300, 250]
        }],
        color: ['#3398DB'],
        grid: {
          top: 70,
          left: 60,
          right: 60,
          bottom: 50
        }
      },
      rankData: [
        {
          no: 1,
          name: '麦当劳',
          money: '323,234'
        },
        {
          no: 2,
          name: '麦当劳',
          money: '323,234'
        },
        {
          no: 3,
          name: '麦当劳',
          money: '323,234'
        },
        {
          no: 4,
          name: '麦当劳',
          money: '323,234'
        },
        {
          no: 5,
          name: '麦当劳',
          money: '323,234'
        },
        {
          no: 6,
          name: '麦当劳',
          money: '323,234'
        },
        {
          no: 7,
          name: '麦当劳',
          money: '323,234'
        }
      ],
      updateData: [
        {
          activeIndex: '1',
          data: [300, 350, 400, 420, 500, 340, 330, 200, 450, 310, 300, 220]
        },
        {
          activeIndex: '2',
          data: [200, 250, 300, 350, 300, 250, 200, 250, 300, 350, 300, 250]
        }
      ]
    }
  },
  // 监听属性 类似于data概念
  computed: {},
  // 监控data中的数据变化
  watch: {},
  // 方法集合
  methods: {
    handleSelect (index) {
      const series = [...this.chartOptions.series]

      series[0].data = this.updateData.find(item => item.activeIndex === index).data
      this.chartOptions = { ...this.chartOptions, series }

      this.activeIndex = index
    }
  }
}
</script>
<style lang="scss" scoped>
//@import url(); 引入公共css类
.center-view {
  margin-top: 20px;
}
.echarts {
  width: 100%;
  height: 100%;
}
.header-wrapper {
  position: relative;
  display: flex;
  flex-direction: row;
  .menu {
    width: 100%;
    padding-left: 20px;
    .el-menu-item {
      height: 50px;
      line-height: 50px;
      margin: 0 20px;
    }
  }
  .wrapper-right {
    position: absolute;
    top: 0;
    right: 20px;
    height: 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }
}

::v-deep .el-card__header {
  border-bottom: none;
  padding: 0;
}

.main-chart-wrapper {
  display: flex;
  height: 270px;
  .chart {
    flex: 0 0 70%;
    width: 70%;
    height: 100%;
  }
  .main-list {
    width: 100%;
    height: 100%;
    overflow: hidden;
    .list-title {
      margin-top: 20px;
      font-size: 12px;
      color: #666;
      font-weight: 500;
    }
    .list-item {
      margin-top: 15px;
      display: flex;
      flex-direction: row;
      align-items: center;
      font-size: 12px;
      height: 20px;
      padding: 6px 20px 6px 0;
      .list-item-no {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 20px;
        height: 20px;
        color: #333;
        &.top-no {
          background-color: #000;
          border-radius: 50%;
          color: #fff;
          font-weight: 500;
        }
      }
      .list-item-name {
        margin-left: 10px;
        color: #333;
      }
      .list-item-money {
        flex: 1;
        text-align: right;
      }
    }
  }
}
</style>
