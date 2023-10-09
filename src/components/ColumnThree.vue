<template>
  <div>
    <div class="title">柱状图——堆叠柱状图+折线</div>
    <div id="main4"></div>
  </div>
</template>

<script>
import * as echarts from "echarts";

export default {
  data() {
    return {
      list: [],
    };
  },
  methods: {
    getData() {
      for (let i = 0; i < 30; i++) {
        let num1 = Math.floor(Math.random() * 200);
        let num2 = Math.floor(Math.random() * 100);
        let total = num1 + num2;
        this.list.push({
          id: i + 1,
          name: "06-" + (i + 1 > 9 ? i + 1 : "0" + (i + 1)),
          num1,
          num2,
          total,
        });
      }
      this.init();
    },
    init() {
      let option = {
        tooltip: {
          trigger: "axis",
          axisPointer: {
            type: "shadow",
          },
        },
        legend: {},
        grid: {
          left: "3%",
          right: "4%",
          bottom: "3%",
          containLabel: true,
        },
        xAxis: [
          {
            type: "category",
            data: this.list.map((item) => item.name),
          },
        ],
        yAxis: [
          {
            type: "value",
          },
        ],
        series: [
          {
            name: "Email",
            type: "bar",
            // 设置同一个 stack 就会堆叠
            stack: "Ad",
            emphasis: {
              focus: "series",
            },
            data: this.list.map((item) => item.num1),
          },
          {
            name: "Union Ads",
            type: "bar",
            stack: "Ad",
            emphasis: {
              focus: "series",
            },
            data: this.list.map((item) => item.num2),
          },
          {
            name: "总计",
            data: this.list.map((item) => item.total),
            type: "line",
          },
        ],
      };
      // 基于准备好的dom，初始化echarts实例
      var myChart = echarts.init(document.getElementById("main4"));
      myChart.setOption(option);
    },
  },
  mounted() {
    this.getData();
  },
};
</script>

<style scoped>
#main4 {
  width: 100%;
  height: 500px;
}
</style>
