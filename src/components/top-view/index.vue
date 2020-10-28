<!--  -->
<template>
  <div class="top-view">
    <el-row :gutter="20">
      <el-col :span="6">
        <el-card shadow="hover">
          <top-sales></top-sales>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          <top-order></top-order>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          <top-user></top-user>
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          <top-total-user></top-total-user>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
// 这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
// 例如：import 《组件名称》 from '《组件路径》';
import TopSales from '@/components/top-sales/index.vue'
import TopUser from '@/components/top-user/index.vue'
import TopOrder from '@/components/top-order/index.vue'
import TopTotalUser from '@/components/top-total-user/index.vue'

export default {
  name: 'TopView',
  components: { TopSales, TopUser, TopOrder, TopTotalUser },
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
</style>
