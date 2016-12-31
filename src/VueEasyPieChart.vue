<template>
  <div class="vue-easy-pie-chart"
       ref="chart"
       :data-percent="percent">
    <div class="inner-text"
         :style="{ fontSize:fontSize,lineHeight:size+'px' }">
      <slot>
        {{percent}}%
      </slot>
    </div>
  </div>
</template>
<style scoped>
  .vue-easy-pie-chart {
    position: relative;
    text-align: center;
  }

  .vue-easy-pie-chart .inner-text {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    text-align: center;
    display: block;
  }
</style>
<script>
  // import $ from 'jquery'
  import EasyPieChart from 'easy-pie-chart'

  export default {
    name: 'VueEasyPieChat',
    data () {
      return {
        pieChart: undefined
      }
    },
    props: {
      barColor: {
        type: String,
        default: "#ef1e25"
      },
      fontSize: {
        type: String,
        default: "20px"
      },
      trackColor: {
        type: String,
        default: "#f2f2f2"
      },
      scaleColor: {type: String, default: "#dfe0e0"},
      scaleLength: {type: Number, default: 5},
      lineCap: {type: String, default: 'round'},
      lineWidth: {type: Number, default: 3},
      size: {type: Number, default: 110},
      rotate: {type: Number, default: 0},
      duration: {type: Number, default: 1000},
      animated: {type: Boolean, default: true},
      percent: {type: Number, default: 0}
    },
    watch: {
      percent(val) {
        this.update(val)
      },
      duration (val) {
        this.pieChart.options.animate.duration = val
        this.update(this.percent)
      },
      animated (val) {
        this.pieChart.options.animate.enabled = val
        this.update(this.percent)
      }
    },
    methods: {
      update (val) {
        this.pieChart.update(val)
      },
      getOptions () {
          return
      }
    },
    mounted() {
      const self = this
      this.pieChart = new EasyPieChart(this.$refs.chart, {
        barColor: this.barColor,
        trackColor: this.trackColor,
        scaleColor: this.scaleColor,
        scaleLength: this.scaleLength,
        lineCap: this.lineCap,
        lineWidth: this.lineWidth,
        size: this.size,
        rotate: this.rotate,
        animate: {
          duration: this.duration,
          enabled: this.animated
        },
        onStart () {
          self.$emit('start')
        },
        onStop () {
          self.$emit('stop')
        },
        onStep () {
          self.$emit('step')
        }
      })

      const addWatcher = propName => {
        this.$watch(propName, (val) => {
          this.pieChart.options[propName] = val
          this.update(this.percent)
        })
      }

      [
        'barColor',
        'trackColor',
        'scaleColor',
        'scaleLength',
        'lineCap',
        'lineWidth',
        'size',
        'rotate'
      ].forEach(addWatcher)

    }
  }
</script>
