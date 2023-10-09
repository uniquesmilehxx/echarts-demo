<template>
  <div>
    <div class="title">柱状图——象形柱图</div>
    <div id="main3"></div>
  </div>
</template>

<script>
import * as echarts from "echarts";

export default {
  methods: {
    init() {
      let option = {
        xAxis: {
          type: "category",
          data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
        },
        yAxis: {
          type: "value",
        },
        series: [
          {
            data: [120, 210, 150, 80, 70, 110, 130],
            type: "pictorialBar", // 图片栏
            showBackground: true,
            backgroundStyle: {
              color: "rgba(180, 180, 180, 0.2)",
            },
            symbolSize: ["80%", "40%"], // 图形的大小，用数组表示宽和高[20, 10]，也可以设置百分比['100%', '100%']表示比例
            symbol: "rect", // 图形类型
            symbolClip: true, // 是否裁剪图形
            symbolRepeat: true, // 指定图形元素是否重复
          },
          {
            type: "bar",
            data: [0, 0, 0, 0, 0, 0, 0],
            showBackground: true,
            backgroundStyle: {
              color: "rgba(180, 180, 180, 0.1)",
            },
          },
        ],
      };
      // 基于准备好的dom，初始化echarts实例
      var myChart = echarts.init(document.getElementById("main3"));
      myChart.setOption(option);
    },
  },
  mounted() {
    this.init();
  },
};
</script>
<style scoped>
#main3 {
  width: 100%;
  height: 500px;
}
</style>
