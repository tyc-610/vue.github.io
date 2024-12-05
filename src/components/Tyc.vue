
<template>
    <div ref="chart" style="width: 200px; height: 100px;"></div>
  </template>
  
  <script>
  import * as echarts from 'echarts';
  
  export default {
    name: 'EChartComponent', // 最好给组件起一个名字
    mounted() {
      // 使用 this.$refs.chart 访问模板中定义的 ref="chart" 元素
      const chartDom = this.$refs.chart;
      const myChart = echarts.init(chartDom);
  
      const option = {
        graphic: {
          elements: [
            {
              type: 'text',
              left: 'center',
              top: 'center',
              style: {
                text: 'Tyc',
                fontSize: 40,
                fontWeight: 'bold',
                fill: 'transparent',
                stroke: '#000',
                lineWidth: 1
              },
              keyframeAnimation: {
                duration: 3000,
                loop: true,
                keyframes: [
                  {
                    percent: 0.7,
                    style: {
                      fill: 'transparent',
                      stroke: '#000',
                      lineWidth: 1,
                      // lineDash 和 lineDashOffset 通常用于创建虚线效果，这里可能不需要
                      // lineDash: [200, 0],
                      // lineDashOffset: 200,
                    }
                  },
                  {
                    percent: 0.8,
                    style: {
                      fill: 'transparent'
                    }
                  },
                  {
                    percent: 1,
                    style: {
                      fill: 'black'
                    }
                  }
                ]
              }
            }
          ]
        }
      };
  
      // 使用配置项和数据显示图表
      myChart.setOption(option);
  
      // 可以在这里保存 myChart 以便后续使用（例如更新图表）
      // 但请注意，通常最好避免在组件的外部直接访问 Vue 组件的内部状态
      // 如果确实需要，可以考虑使用 Vuex 或其他状态管理解决方案
      // this.myChart = myChart; // 不推荐这样做，除非你有特别的理由
    },
    // 如果需要在组件销毁时做一些清理工作（例如销毁 ECharts 实例），
    // 可以在 beforeDestroy 生命周期钩子中添加代码
    beforeUnmount() {
      // 如果 myChart 被保存为组件的属性，则可以在这里销毁它
      // 但由于我们在上面的代码中没有保存它，所以这里不需要做任何事
      // if (this.myChart) {
      //   this.myChart.dispose();
      // }
    }
  };
  </script>
  
  <style scoped>
  /* 你可以在这里添加组件的样式 */
  </style>