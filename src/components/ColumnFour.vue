<template>
  <div>
    <div class="title">柱状图——堆叠柱状图+象形柱图</div>
    <div id="main5"></div>
  </div>
</template>

<script>
import * as echarts from "echarts";

var myData = ["大栅栏", "天安门", "故宫", "景山", "北海公园"];
var databeast = [389, 259, 262, 324, 232];
var databeauty = [280, 128, 255, 254, 313];

// 设置为总数
databeast.forEach((item, index) => {
  databeast[index] = item + databeauty[index];
});

const option = {
  xAxis: {
    type: "category",
    axisLine: {
      show: true,
    },
    axisTick: {
      show: false,
    },
    axisLabel: {
      show: true,
      margin: 8,
      textStyle: {
        color: "#9D9EA0",
        fontSize: 12,
      },
    },
    data: myData,
  },
  yAxis: {
    type: "value",
    axisLine: {
      show: true,
    },
    //y轴分割线
    axisTick: {
      show: false,
    },
    position: "center",
    //y轴标签
    axisLabel: {
      show: true,
    },
    splitLine: {
      show: false,
      lineStyle: {
        color: "#1F2022",
        width: 1,
        type: "solid",
      },
    },
  },
  series: [
    // 展示总数，带颜色
    {
      type: "pictorialBar",
      symbol: "rect",
      itemStyle: {
        normal: {
          color: "red",
        },
      },
      symbolRepeat: "fixed",
      symbolClip: true,
      symbolMargin: 2,
      symbolSize: [20, 10],
      data: databeast,
    },
    // 展示其中一个数量，带颜色
    // 出来的视觉效果就是，这个压在总数上面，所以会有分层效果
    {
      type: "pictorialBar",
      symbol: "rect",
      itemStyle: {
        normal: {
          color: "green",
        },
      },
      symbolRepeat: "fixed",
      symbolClip: true,
      symbolMargin: 2,
      symbolSize: [20, 10],
      data: databeauty,
    },
    // 展示总数，展示浅色且带有透明度
    // 效果就是背景色
    {
      type: "pictorialBar",
      itemStyle: {
        normal: {
          color: "rgba(82,110,63,0.2)",
        },
      },
      label: {
        normal: {
          show: false,
        },
      },
      symbolRepeat: "fixed",
      symbolMargin: 2,
      symbol: "rect",
      symbolSize: [20, 10],
      data: databeast,
      z: 99999,
    },
  ],
};

export default {
  methods: {
    init() {
      // 基于准备好的dom，初始化echarts实例
      var myChart = echarts.init(document.getElementById("main5"));
      myChart.setOption(option);
    },
  },
  mounted() {
    this.init();
  },
};
</script>

<style scoped>
#main5 {
  width: 100%;
  height: 500px;
}
</style>
