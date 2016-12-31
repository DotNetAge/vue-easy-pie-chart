<template>
  <div id="app" class="uk-container uk-container-center">
    <h1 class="uk-heading-large">vue-easy-pie-chart playground</h1>
    <hr/>
    <div class="uk-grid">
      <div class="uk-width-1-2">
        <div class="uk-panel">
          <h3 class="uk-panel-title">Preview</h3>
          <vue-easy-pie-chart :percent="percent"
                              :bar-color="barColor"
                              :track-color="trackColor"
                              :scale-color="scaleColor"
                              :line-cap="lineCap"
                              :line-width="lineWidth"
                              :scale-length="scaleLength"
                              :size="size"
                              :rotate="rotate"
                              :font-size="fontSize">
          </vue-easy-pie-chart>
        </div>
      </div>
      <div class="uk-width-1-2">
        <div class="uk-panel">

          <h3 class="uk-panel-title">Attributes</h3>
          <div class="uk-form uk-form-stacked uk-column-medium-1-2">
            <div class="uk-form-row">
              <label class="uk-form-label">percent</label>
              <input v-model="percent" type="number"/>
            </div>
            <div class="uk-form-row">
              <label class="uk-form-label">barColor</label>
              <input v-model="barColor"/>
            </div>
            <div class="uk-form-row">
              <label class="uk-form-label">trackColor</label>
              <input v-model="trackColor"/>
            </div>
            <div class="uk-form-row">
              <label class="uk-form-label">scaleColor</label>
              <input v-model="scaleColor"/>
            </div>
            <div class="uk-form-row">
              <label class="uk-form-label">scaleLength</label>
              <input v-model="scaleLength" type="number"/>
            </div>
            <div class="uk-form-row">
              <label class="uk-form-label">lineCap</label>
              <select v-model="lineCap">
                <option>round</option>
                <option>butt</option>
                <option>square</option>
              </select>
            </div>
            <div class="uk-form-row">
              <label class="uk-form-label">lineWidth</label>
              <input v-model="lineWidth" type="number"/>
            </div>
            <div class="uk-form-row">
              <label class="uk-form-label">fontSize</label>
              <input v-model="fontSize"/>
            </div>
            <div class="uk-form-row">
              <label class="uk-form-label">size</label>
              <input v-model="size" type="number"/>
            </div>
            <div class="uk-form-row">
              <label class="uk-form-label">rotate</label>
              <input v-model="rotate" type="number"/>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="uk-grid">
      <div class="uk-width-1-1">
        <div class="uk-panel uk-panel-header">
          <h3 class="uk-panel-title">HTML</h3>
          <pre><code lang="html">&lt;vue-easy-pie-chart
            :percent="{{percent}}"
            :bar-color="{{barColor}}"
            :track-color="{{trackColor}}"
            :scale-color="{{scaleColor}}"
            :line-cap="{{lineCap}}"
            :line-width="{{lineWidth}}"
            :scale-length="{{scaleLength}}"
            :size="{{size}}"
            :rotate="{{rotate}}"
            :font-size="{{fontSize}}"&gt;
&lt;/vue-easy-pie-chart&gt;
            </code>
          </pre>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  //import VueEasyPieChart from './VueEasyPieChart'
  import VueEasyPieChart from '../dist/vui-easy-pie-chart.common'
  import '../dist/vui-easy-pie-chart.css'
  import 'uikit/dist/css/uikit.css'
  import 'uikit/dist/css/uikit.almost-flat.css'
  export default {
    name: 'app',
    data () {
      return {
        percent: 20,
        barColor: "#ef1e25",
        trackColor: "#f2f2f2",
        scaleColor: "#dfe0e0",
        scaleLength: 5,
        lineCap: "round",
        lineWidth: 3,
        size: 210,
        rotate: 0,
        fontSize: "20px"
      }
    },
    components: {
      VueEasyPieChart
    }
  }
</script>
