<!--  -->
<template>
  <div class="bottom-view">
    <!-- Left Card -->
    <div class="view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">关键字搜索</div>
        </template>
        <template>
          <div class="main-wrapper">
            <div class="chart-wrapper">
              <div class="chart">
                <div class="chart-title">搜索用户数</div>
                <div class="chart-data">96,634</div>
                <v-chart :options="searchUserOptions"></v-chart>
              </div>
              <div class="chart">
                <div class="chart-title">搜索量</div>
                <div class="chart-data">198,781</div>
                <v-chart :options="searchNumOptions"></v-chart>
              </div>
            </div>
            <div class="table-wrapper">
              <el-table :data="showPage">
                <el-table-column
                  prop="rank"
                  width="180"
                  label="排名"
                ></el-table-column>
                <el-table-column
                  prop="keyword"
                  width="180"
                  label="关键字"
                ></el-table-column>
                <el-table-column
                  prop="count"
                  label="总搜索量"
                ></el-table-column>
                <el-table-column
                  prop="users"
                  label="搜索用户数"
                ></el-table-column>
              </el-table>
            </div>
            <div class="pagination">
              <el-pagination
                layout="prev, pager, next"
                :total="13"
                :page-size="4"
                background
                @current-change="changePage"
              ></el-pagination>
            </div>
          </div>
        </template>
      </el-card>
    </div>
    <!-- Right Card -->
    <div class="view" style="margin-left: 10px;">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">
            <div class="title">分离销售排行</div>
            <div class="radio-wrapper">
              <el-radio-group v-model="radioSelect" @change="handleChangeSelect" size="small">
                <el-radio-button label="品类" />
                <el-radio-button label="商品" />
              </el-radio-group>
            </div>
          </div>
        </template>
        <template>
          <div class="chart-category">
            <div class="demo">
              <v-chart
                width="100%"
                height="100%"
                :options="categoryOptions"
              ></v-chart>
            </div>
          </div>
        </template>
      </el-card>
    </div>
  </div>
</template>

<script>
// 这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
// 例如：import 《组件名称》 from '《组件路径》';

export default {
  name: 'BottomView',
  components: {},
  data () {
    // 这里存放数据
    return {
      searchUserOptions: {
        xAxis: {
          type: 'category',
          boundaryGap: false
        },
        yAxis: {
          show: false
        },
        series: [
          {
            type: 'line',
            data: [100, 150, 290, 250, 250, 100, 150, 50, 150, 100],
            areaStyle: {
              color: 'rgba(95, 187, 255, .5)'
            },
            lineStyle: {
              color: 'rgba(95,187,255)'
            },
            itemStyle: {
              opacity: 0
            },
            smooth: true
          }
        ],
        grid: {
          top: 0,
          left: 0,
          bottom: 0,
          right: 0
        }
      },
      searchNumOptions: {
        xAxis: {
          type: 'category',
          boundaryGap: false
        },
        yAxis: {
          show: false,
          min: 0,
          max: 550
        },
        series: [
          {
            type: 'line',
            data: [500, 440, 110, 450, 220, 240, 260, 340, 460, 100],
            areaStyle: {
              color: 'rgba(95, 187, 255, .5)'
            },
            lineStyle: {
              color: 'rgba(95,187,255)'
            },
            itemStyle: {
              opacity: 0
            },
            smooth: true
          }
        ],
        grid: {
          top: 0,
          left: 0,
          bottom: 0,
          right: 0
        }
      },
      radioSelect: '品类',
      tabList: [
        {
          id: 1,
          rank: 1,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 2,
          rank: 2,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 3,
          rank: 3,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 4,
          rank: 4,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 5,
          rank: 5,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 6,
          rank: 6,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 7,
          rank: 7,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 8,
          rank: 8,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 9,
          rank: 9,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 10,
          rank: 10,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 11,
          rank: 11,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 12,
          rank: 12,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        },
        {
          id: 13,
          rank: 13,
          keyword: '北京',
          count: 100,
          users: 90,
          range: '90%'
        }
      ],
      currentPage: 1

    }
  },
  // 监听属性 类似于data概念
  computed: {
    showPage () {
      const start = (this.currentPage - 1) * 4
      const arr = []
      for (let i = 0; i < 4; i++) {
        arr.push(start + i)
      }

      const pages = this.tabList.filter((item, index) => arr.includes(index))
      return pages
    },
    categoryMockData1 () {
      return [
        {
          legendname: '粉面粥店',
          value: 67,
          percent: '15.40%',
          itemStyle: { color: '#e7e702' },
          name: '粉面粥店'
        },
        {
          legendname: '简餐便当',
          value: 97,
          percent: '22.30%',
          itemStyle: { color: '#9d7fec' },
          name: '简餐便当 '
        },
        {
          legendname: '简餐便当3',
          value: 97,
          percent: '22.30%',
          itemStyle: { color: '#9d7f3c' },
          name: '简餐便当3'
        },
        {
          legendname: '简餐便当4',
          value: 97,
          percent: '22.30%',
          itemStyle: { color: '#9d7ff9' },
          name: '简餐便当4'
        },
        {
          legendname: '简餐便当5',
          value: 97,
          percent: '22.30%',
          itemStyle: { color: '#9d7f88' },
          name: '简餐便当5'
        },
        {
          legendname: '汉堡披萨',
          value: 92,
          percent: '21.15%',
          itemStyle: { color: '#5085f2' },
          name: '汉堡披萨'
        }
      ]
    },
    categoryMockData2 () {
      return [
        {
          legendname: '粉面粥店',
          value: 87,
          percent: '20.40%',
          itemStyle: { color: '#e7e702' },
          name: '粉面粥店'
        },
        {
          legendname: '简餐便当',
          value: 117,
          percent: '26.30%',
          itemStyle: { color: '#9d7fec' },
          name: '简餐便当 '
        },
        {
          legendname: '简餐便当3',
          value: 117,
          percent: '26.30%',
          itemStyle: { color: '#9d7f3c' },
          name: '简餐便当3'
        },
        {
          legendname: '简餐便当4',
          value: 123,
          percent: '22.30%',
          itemStyle: { color: '#9d7ff9' },
          name: '简餐便当4'
        },
        {
          legendname: '简餐便当5',
          value: 123,
          percent: '22.30%',
          itemStyle: { color: '#9d7f88' },
          name: '简餐便当5'
        },
        {
          legendname: '汉堡披萨',
          value: 156,
          percent: '21.15%',
          itemStyle: { color: '#5085f2' },
          name: '汉堡披萨'
        }
      ]
    },
    categoryOptions () {
      return {
        title: [
          {
            text: this.radioSelect === '品类' ? '品类分布' : '商品分布',
            textStyle: { fontSize: 14, color: '#666' },
            left: 20,
            top: 20
          },
          {
            text: '累计订单数',
            subtext: '320',
            x: '38.5%',
            y: '42.5%',
            textAlign: 'center',
            textStyle: { fontSize: 14, color: '#999' },
            subtextStyle: { fontSize: 28, color: '#333' }
          }
        ],
        series: [
          {
            type: 'pie',
            data: this.radioSelect === '品类' ? this.categoryMockData1 : this.categoryMockData2,
            name: '品类分布',
            label: {
              normal: {
                show: true,
                position: 'outter',
                formatter: function (params) {
                  return `${params.data.legendname}（${params.data.percent}）`
                }
              }
            },
            center: ['40%', '50%'],
            radius: ['45%', '60%'],
            labelLine: {
              normal: {
                length: 5,
                length2: 3,
                smooth: true
              }
            },
            clockwise: false,
            itemStyle: {
              borderWidth: 4,
              borderColor: '#fff'
            }
          }
        ],
        legend: {
          type: 'scroll',
          orient: 'vertical',
          height: 258,
          left: '82%',
          top: 'middle'
        },
        tooltip: {
          trigger: 'item',
          formatter: function (params) {
            const str = params.seriesName
            return `${str}<br/>${params.marker} ${params.data.legendname} <br/>数量：${params.data.value}<br/>占比：${params.data.percent}`
          }
        }
      }
    }
  },
  // 监控data中的数据变化
  watch: {},
  mounted () {

  },
  // 方法集合
  methods: {
    changePage (index) {
      this.currentPage = index
    }

  }
}
</script>
<style lang="scss" scoped>
//@import url(); 引入公共css类
.bottom-view {
  display: flex;
  flex-direction: row;
  margin-top: 20px;
  .view {
    flex: 1;
    width: 50%;
    box-sizing: border-box;
    .title-wrapper {
      display: flex;
      flex-direction: row;
      height: 60px;
      box-sizing: border-box;
      justify-content: space-between;
      align-items: center;
      font-size: 14px;
      font-weight: 500;
      padding: 0 0 0 20px;
      .title {
        padding-right: 20px;
      }
    }
  }
  .chart-wrapper {
    display: flex;
    flex-direction: row;
    padding: 0 10px;
    margin-top: 20px;
    .chart {
      flex: 1;
      padding: 0 20px;
      .chart-title {
        color: #999;
        font-size: 14px;
      }
      .chart-data {
        font-size: 22px;
        color: #333;
        font-weight: 500;
        letter-spacing: 2px;
      }
      .echarts {
        width: 100%;
        height: 50px !important;
      }
    }
    .table-wrapper {
      flex: 1;
      margin-top: 20px;
      padding: 0 20px 20px 20px;
    }
  }
  .pagination {
    display: flex;
    justify-content: flex-end;
    margin-top: 20px;
  }
}
// right card
.echarts {
  width: 100% !important;
  height: 100% !important;
}
.chart-category {
  height: 410px;
  display: flex;
  .demo {
    flex: 1;
  }
}
</style>
