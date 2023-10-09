<template>
  <div>
    <div class="title">3D柱状图——中间圆柱，上下盖子</div>
    <div id="main"></div>
    <div class="title">3D柱状图——中间能看到棱柱，自定义shape</div>
    <div id="main2"></div>
  </div>
</template>

<script>
/**
 *  x轴、y轴数据同理
 *  xAxis.type = 'category'：类目轴，适用于离散的类目数据
 *  xAxis.data：类目数据，在类目轴（type: 'category'）中有效
 *  yAxis.axisLine：坐标轴轴线相关设置
 *  yAxis.axisTick：坐标轴刻度相关设置
 *
 *
 *
 */
import * as echarts from "echarts";

export default {
  data() {
    return {};
  },
  methods: {
    initColumn1() {
      let option = {
        // 背景色
        backgroundColor: "#031245",
        // 全局的字体样式
        textStyle: {
          color: "#c0c3cd",
          fontSize: 14,
        },
        // 工具栏
        toolbox: {
          // 是否显示工具栏组件
          show: false,
          // 各工具配置项。
          feature: {
            // 保存为图片
            saveAsImage: {
              // 保存的图片背景色
              backgroundColor: "#031245",
            },
            // 配置项还原
            restore: {},
          },
          // 公用的 icon 样式设置
          iconStyle: {
            // 图形的描边颜色
            borderColor: "#c0c3cd",
          },
        },
        // 图例组件
        legend: {
          // 图例组件离容器上侧的距离（像素值或对齐值）
          top: 10,
          // 图例标记的图形宽度
          itemWidth: 8,
          // 图例标记的图形高度
          itemHeight: 8,
          // 图例项的 icon
          icon: "circle",
          // 图例组件离容器左侧的距离（像素值或对齐值）
          left: "center",
          // 图例内边距，单位px（例：padding: 5；padding: [5, 10]；padding: [5, 10, 5, 10]）
          padding: 0,
          // 图例的公用文本样式
          textStyle: {
            color: "#c0c3cd",
            fontSize: 14,
            // 文字块的内边距
            padding: [2, 0, 0, 0],
          },
        },
        // 调色盘颜色列表。如果系列没有设置颜色，则会依次循环从该列表中取颜色作为系列颜色
        color: ["#00D7E9", "rgba(0, 215, 233, 0.9)"],
        // 直角坐标系内绘图网格
        grid: {
          // grid 区域是否包含坐标轴的刻度标签
          containLabel: true,
          // grid 组件离容器左侧的距离
          left: 20,
          // grid 组件离容器右侧的距离
          right: 20,
          // grid 组件离容器下侧的距离
          bottom: 10,
          // grid 组件离容器上侧的距离
          top: 40,
        },
        // x 轴
        xAxis: {
          // 坐标轴名称的文字样式
          nameTextStyle: {
            color: "#c0c3cd",
            // 文字块的内边距
            padding: [0, 0, -10, 0],
            fontSize: 14,
          },
          // 坐标轴【刻度标签】的相关设置
          axisLabel: {
            color: "#c0c3cd",
            fontSize: 14,
            // 坐标轴刻度标签的显示间隔，在类目轴中有效
            interval: 0,
          },
          // 【刻度】相关设置
          axisTick: {
            show: false,
            lineStyle: {
              color: "#384267",
              width: 1,
            },
          },
          // 坐标轴在 grid 区域中的分隔线
          splitLine: {
            show: false,
          },
          // 坐标轴【轴线】相关设置
          axisLine: {
            lineStyle: {
              color: "#335971",
            },
            show: false,
          },
          // 类目数据，在类目轴（type: 'category'）中有效。
          data: ["1月", "2月", "3月", "4月", "5月", "6月"],
          // 'category' 类目轴，适用于离散的类目数据
          type: "category",
        },
        // 直角坐标系 grid 中的 y 轴
        yAxis: {
          // 坐标轴名称的文字样式
          nameTextStyle: {
            color: "#c0c3cd",
            // 文字块的内边距
            padding: [0, 0, -10, 0],
            fontSize: 14,
          },
          // 坐标轴【刻度标签】的相关设置
          axisLabel: {
            color: "#c0c3cd",
            fontSize: 14,
          },
          // 坐标轴【刻度】相关设置
          axisTick: {
            lineStyle: {
              color: "#668092",
              width: 1,
            },
            show: true,
          },
          // 坐标轴在 grid 区域中的分隔线
          splitLine: {
            show: true,
            lineStyle: {
              color: "#335971",
              type: "dashed",
            },
          },
          // 坐标轴【轴线】相关设置
          axisLine: {
            lineStyle: {
              color: "#668092",
              width: 1,
              // type: "dashed",
            },
            show: true,
          },
          // 坐标轴名称
          name: "",
        },
        // 系列
        series: [
          // 圆柱
          {
            // 柱状图
            type: "bar",
            // 系列中的数据内容数组。数组项通常为具体的数据项。
            data: [200, 85, 112, 275, 305, 415],
            // 柱条的最大宽度
            barMaxWidth: "auto",
            // 柱条的最小宽度
            barWidth: 30,
            // 图形样式
            itemStyle: {
              // 柱条的颜色。 默认从全局调色盘 option.color 获取颜色
              color: {
                // 线性渐变，前四个参数分别是 x0, y0, x2, y2, 范围从 0 - 1，相当于在图形包围盒中的百分比，
                // 如果 globalCoord 为 `true`，则该四个值是绝对的像素位置
                x: 0,
                y: 0,
                x2: 0,
                y2: 1,
                type: "linear",
                colorStops: [
                  // 0% 处的颜色
                  {
                    offset: 0,
                    // color: "#0D5EB1",
                    color: "green",
                  },
                  // 100% 处的颜色
                  {
                    offset: 1,
                    // color: "#00D7E9",
                    color: "red",
                  },
                ],
              },
            },
            // 图形上的文本标签，可用于说明图形的一些数据信息，比如值，名称等。
            label: {
              show: true,
              position: "top",
              // 距离图形元素的距离
              distance: 10,
              color: "#fff",
            },
          },
          // 圆柱的底
          {
            // 象形柱图：是可以设置各种具象图形元素（如图片、SVG PathData 等）的柱状图
            type: "pictorialBar",
            // 系列中的数据内容数组。数组项通常为具体的数据项。
            data: [1, 1, 1, 1, 1, 1],
            // 柱条的最大宽度
            barMaxWidth: "20",
            // 图形类型：菱形
            symbol: "diamond",
            // 图形相对于原本位置的偏移
            // 可以设置成绝对值（如 10），也可以设置成百分比（如 '120%'、['55%', 23]）
            // 当设置为百分比时，表示相对于自身尺寸 symbolSize 的百分比
            // [0, '50%'] 就是把图形向下移动了自身尺寸的一半的位置。
            symbolOffset: [0, "50%"],
            // 图形的大小，数字表大小，百分比表比例
            symbolSize: [30, 15],
          },
          // 圆柱的盖子
          {
            type: "pictorialBar",
            data: [200, 85, 112, 275, 305, 415],
            barMaxWidth: "20",
            symbolPosition: "end",
            symbol: "diamond",
            // [0, '-50%'] 就是把图形向上移动了自身尺寸的一半的位置。
            symbolOffset: [0, "-50%"],
            symbolSize: [30, 12],
            // 象形柱图所有图形的 zlevel 值
            // 用于 Canvas 分层，不同zlevel值的图形会放置在不同的 Canvas 中
            zlevel: 2,
          },
        ],
        // 提示框组件
        tooltip: {
          show: true,
          // 提示框浮层内容格式器，支持字符串模板和回调函数两种形式
          // 请参考：https://echarts.apache.org/zh/option.html#tooltip.formatter
          formatter: "{b0}: {c0}", // b 类目值   c 数值
          // formatter: (datam) => {
          //   console.log("datam-----", datam);
          //   return `${datam.name}：${datam.value}`;
          // },
        },
      };
      // 基于准备好的dom，初始化echarts实例
      var myChart = echarts.init(document.getElementById("main"));
      myChart.setOption(option);
    },
    initColumn2() {
      // echarts.graphic.extendShape：创建一个新的 shape class。
      //    - ShapeClass 须用 echarts.graphic.extendShape 生成。 注册后，这个 class 可以用 echarts.graphic.getShapeClass 方法得到。
      //    - registerShape 会覆盖已注册的 class，如果用相同的 name 的话。
      //    - 注册的 class，可以被用于 自定义系列（custom series） 和 图形组件（graphic component），声明 {type: name} 即可

      // 头疼，难懂
      // 绘制左侧面
      const CubeLeft = echarts.graphic.extendShape({
        shape: {
          x: 0,
          y: 0,
        },
        buildPath: function (ctx, shape) {
          console.log("shape---------", shape);
          // 会canvas的应该都能看得懂，shape是从custom传入的
          const xAxisPoint = shape.xAxisPoint;
          const c0 = [shape.x, shape.y];
          const c1 = [shape.x - 13, shape.y - 13];
          const c2 = [xAxisPoint[0] - 13, xAxisPoint[1] - 13];
          const c3 = [xAxisPoint[0], xAxisPoint[1]];
          console.log("left--------", c0, c1, c2, c3);
          ctx
            .moveTo(c0[0], c0[1])
            .lineTo(c1[0], c1[1])
            .lineTo(c2[0], c2[1])
            .lineTo(c3[0], c3[1])
            .closePath();
        },
      });
      // 绘制右侧面
      const CubeRight = echarts.graphic.extendShape({
        shape: {
          x: 0,
          y: 0,
        },
        buildPath: function (ctx, shape) {
          console.log("shape---------", shape);
          const xAxisPoint = shape.xAxisPoint;
          const c1 = [shape.x, shape.y];
          const c2 = [xAxisPoint[0], xAxisPoint[1]];
          const c3 = [xAxisPoint[0] + 18, xAxisPoint[1] - 9];
          const c4 = [shape.x + 18, shape.y - 9];
          console.log("right--------", c1, c2, c3, c4);
          ctx
            .moveTo(c1[0], c1[1])
            .lineTo(c2[0], c2[1])
            .lineTo(c3[0], c3[1])
            .lineTo(c4[0], c4[1])
            .closePath();
        },
      });
      // 绘制顶面
      const CubeTop = echarts.graphic.extendShape({
        shape: {
          x: 0,
          y: 0,
        },
        buildPath: function (ctx, shape) {
          const c1 = [shape.x, shape.y];
          const c2 = [shape.x + 18, shape.y - 9];
          const c3 = [shape.x + 5, shape.y - 22];
          const c4 = [shape.x - 13, shape.y - 13];
          ctx
            .moveTo(c1[0], c1[1])
            .lineTo(c2[0], c2[1])
            .lineTo(c3[0], c3[1])
            .lineTo(c4[0], c4[1])
            .closePath();
        },
      });
      // 注册三个面图形
      echarts.graphic.registerShape("CubeLeft", CubeLeft);
      echarts.graphic.registerShape("CubeRight", CubeRight);
      echarts.graphic.registerShape("CubeTop", CubeTop);

      const MAX = [800, 800, 800, 800, 800, 800, 800];
      const VALUE = [210.9, 260.8, 204.2, 504.9, 740.5, 600.3, 119.0];
      let option = {
        backgroundColor: "#012366",
        tooltip: {
          trigger: "axis",
          axisPointer: {
            type: "shadow",
          },
          formatter: function (params) {
            const item = params[1];
            return item.name + " : " + item.value;
          },
        },
        grid: {
          left: 40,
          right: 40,
          bottom: 100,
          top: 100,
          containLabel: true,
        },
        xAxis: {
          type: "category",
          data: ["1月", "2月", "3月", "4月", "5月", "6月", "7月"],
          axisLine: {
            show: true,
            lineStyle: {
              color: "white",
            },
          },
          offset: 25,
          axisTick: {
            show: false,
            length: 9,
            alignWithLabel: true,
            lineStyle: {
              color: "#7DFFFD",
            },
          },
          axisLabel: {
            show: true,
            fontSize: 16,
          },
        },
        yAxis: {
          min: 0,
          max: 1200,
          interval: 200,
          type: "value",
          axisLine: {
            show: false,
            lineStyle: {
              color: "white",
            },
          },
          splitLine: {
            show: true,
            lineStyle: {
              type: "dashed",
              color: "rgba(255,255,255,0.1)",
            },
          },
          axisTick: {
            show: false,
          },
          axisLabel: {
            show: true,
            fontSize: 16,
          },
          boundaryGap: ["20%", "20%"],
        },
        series: [
          // type: "custom"：自定义系列中的图形元素渲染
          // 最高的柱子
          {
            type: "custom",
            data: MAX,
            // 请参考：https://echarts.apache.org/zh/option.html#series-custom.renderItem
            // 1、renderItem 函数提供了两个参数：
            //   -  params：包含了当前数据信息和坐标系的信息。
            //   -  api：是一些开发者可调用的方法集合。
            // 2、renderItem 函数须返回根据此 dataItem 绘制出的图形元素的定义信息
            renderItem: function (params, api) {
              console.log("api.value----", api.value(0), api.value(1));
              // api.value：得到给定维度的数据值
              // api.coord：将数据值映射到坐标系上，至少包含：[x, y]，对于 polar坐标系，还会包含其他信息：[x, y, radius, angle]
              // 所以 location 是实际的坐标 [ x,y ]
              const location = api.coord([api.value(0), api.value(1)]);
              console.log("location-----", location);
              console.log("xAxisPoint------", api.coord([api.value(0), 0]));
              return {
                // group 是唯一的可以有子节点的容器。group 可以用来整体定位一组图形元素
                type: "group",
                children: [
                  {
                    type: "CubeLeft",
                    // 此处的 shape 会传入 CubeLeft 中
                    shape: {
                      api,
                      x: location[0],
                      y: location[1],
                      xAxisPoint: api.coord([api.value(0), 0]),
                    },
                    style: {
                      fill: "rgba(47,102,192,.27)",
                    },
                  },
                  {
                    type: "CubeRight",
                    shape: {
                      api,
                      x: location[0],
                      y: location[1],
                      xAxisPoint: api.coord([api.value(0), 0]),
                    },
                    style: {
                      fill: "rgba(59,128,226,.27)",
                    },
                  },
                  {
                    type: "CubeTop",
                    shape: {
                      api,
                      x: location[0],
                      y: location[1],
                      xAxisPoint: api.coord([api.value(0), 0]),
                    },
                    style: {
                      fill: "rgba(72,156,221,.27)",
                    },
                  },
                ],
              };
            },
          },
          // 各自的小柱子
          {
            type: "custom",
            renderItem: (params, api) => {
              const location = api.coord([api.value(0), api.value(1)]);
              var color =
                api.value(1) > 800
                  ? "red"
                  : new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                      {
                        offset: 0,
                        color: "rgba(37,170,254,1)",
                      },
                      {
                        offset: 0.8,
                        color: "rgba(37,170,254,0.1)",
                      },
                    ]);
              console.log(
                "xValue-----------",
                api.value(0),
                api.value(1),
                location[0],
                location[1],
                api.coord([api.value(0), 0])
              );
              return {
                type: "group",
                children: [
                  {
                    type: "CubeLeft",
                    shape: {
                      api,
                      xValue: api.value(0),
                      yValue: api.value(1),
                      x: location[0],
                      y: location[1],
                      xAxisPoint: api.coord([api.value(0), 0]),
                    },
                    style: {
                      fill: color,
                    },
                  },
                  {
                    type: "CubeRight",
                    shape: {
                      api,
                      xValue: api.value(0),
                      yValue: api.value(1),
                      x: location[0],
                      y: location[1],
                      xAxisPoint: api.coord([api.value(0), 0]),
                    },
                    style: {
                      fill: color,
                    },
                  },
                  {
                    type: "CubeTop",
                    shape: {
                      api,
                      xValue: api.value(0),
                      yValue: api.value(1),
                      x: location[0],
                      y: location[1],
                      xAxisPoint: api.coord([api.value(0), 0]),
                    },
                    style: {
                      fill: color,
                    },
                  },
                ],
              };
            },
            data: VALUE,
          },
          // 柱状图（仅展示label）
          {
            type: "bar",
            // 设置为透明，即隐藏柱子
            itemStyle: {
              color: "transparent",
            },
            // 仅用来展示label
            label: {
              normal: {
                show: true,
                position: "top",
                fontSize: 16,
                color: "#fff",
                offset: [2, -25],
              },
            },
            tooltip: {},
            // 全展示800
            data: MAX,
          },
        ],
      };
      // 基于准备好的dom，初始化echarts实例
      var myChart = echarts.init(document.getElementById("main2"));
      myChart.setOption(option);
    },
  },
  mounted() {
    this.initColumn1();
    this.initColumn2();
  },
};
</script>
<style scoped>
#main {
  width: 100%;
  height: 300px;
}
#main2 {
  width: 100%;
  height: 400px;
}
</style>
