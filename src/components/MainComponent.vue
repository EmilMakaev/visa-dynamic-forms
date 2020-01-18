<template>
  <div>
    <div class="workspace">
      <keep-alive>
        <component
          ref="currentStep"
          :is="currentStep" 
          @update="processStep"
          :all-data="form"
        ></component>
      </keep-alive>

      <div class="progress-bar">
        <div :style="`width: ${progress}%;`"></div>
      </div>
      <div class="buttons">
        <button
          @click="goNext"
          :disabled="!canGoNext"
          class="button-next btn"
        >Next
        </button>
        <button
          @click="goBack"
          v-if="currentStepNumber > 1"
          class="button-back btn"
        >Back
        </button>
        
      </div>
    </div>
   <!--  <pre><code>{{form}}</code></pre> -->
  </div>
</template>

<script>
import CountryDurationGoal from './CountryDurationGoal'
import NameAndPhone from './NameAndPhone'
import CheckData from './CheckData'
import DataReceived from './DataReceived'

export default {
  name: 'maincomponent',
  components: {
    CountryDurationGoal,
    NameAndPhone,
    CheckData,
    DataReceived
  },
  data () {
    return {
      currentStepNumber: 1,
      canGoNext: false,
      steps: [
        'CountryDurationGoal',
        'NameAndPhone',
        'CheckData',
        'DataReceived'
      ],
      form: {
        country: null,
        duration: null,
        goal: null,
        name: null,
        phone: null,
        time: null
      }
    }
  },
  computed: {
    length () {
      return this.steps.length
    },
    currentStep () {
      return this.steps[this.currentStepNumber - 1]
    },
    progress () {
      return this.currentStepNumber/this.length * 100
    }
  },
  methods: {
    processStep(stepData) {
      Object.assign(this.form, stepData)
      this.canGoNext = true
    },
    goBack () {
      this.currentStepNumber--
      this.canGoNext = true
    },
    goNext () {
      this.currentStepNumber++
      this.canGoNext = false
      /* this.$nextTick(() => {
        this.$refs.currentStep.submit()
      }) */
    }
  }
}
</script>