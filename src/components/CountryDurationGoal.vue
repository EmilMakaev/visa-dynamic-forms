<template>
  <div id="CountryDurationGoal">
    <h1>{{ h1 }}</h1>
    <div @change="submit" class="options">
      <div class="option">
        <p class="description">1. Select a country</p>
        <select 
          v-model="selectedCountry"
          placeholder="Your destination country"
        >
          <option 
            disabled
            value=""
          >Choose country</option>
          <option
            v-for="country in countries"
            :value="country.description"
          > {{ country.description }} </option>
        </select>
      </div>

      <div class="option">
        <p class="description">2. Choose a visa expiration date</p>
        <div class="option-purposes">
          <div class="option-purpose">
            <input 
              type="radio" 
              id="one" 
              value="Up to 6 months" 
              v-model="picked"
              
            >
            <label for="one">Up to 6 months</label>
          </div>
          <div class="option-purpose">
            <input 
              type="radio" 
              id="two" 
              value="Up to 1 year" 
              v-model="picked"
              
            >
            <label for="two">Up to 1 years</label>
          </div>
          <div class="option-purpose">
            <input 
              type="radio" 
              id="three" 
              value="Up to 3 years" 
              v-model="picked"
            >
            <label for="three">Up to 3 years</label>
          </div>
          <div class="option-purpose">
            <input 
              type="radio" 
              id="four" 
              value="Up to 5 years" 
              v-model="picked"
            >
            <label for="four">Up to 5 years</label>
          </div>
        </div>
      </div>

      <div class="option">
        <p class="description">3. Choose a visit purpose</p>
        <div class="option-purposes">
          <div class="option-purpose">
            <input 
              type="radio" 
              id="one1" 
              value="Tourism" 
              v-model="picked2"
              
            >
            <label for="one1">Tourism</label>
          </div>
          <div class="option-purpose">
            <input type="radio" id="two2" value="Treatment" v-model="picked2">
            <label for="two2">Treatment</label>
          </div>
          <div class="option-purpose">
            <input type="radio" id="three3" value="Work" v-model="picked2">
            <label for="three3">Work</label>
          </div>
          <div class="option-purpose">
            <input type="radio" id="four4" value="Study" v-model="picked2">
            <label for="four4">Study</label>
          </div>
        </div>
      </div>
      <div class="option option4">
        <p><span class="description">Country:</span> {{ selectedCountry }}</p>  
        <p><span class="description">Duration:</span> {{ picked }}</p>
        <p><span class="description">Goal:</span> {{ picked2 }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      countries: '',
      selectedCountry: '',
      picked: '',
      picked2: '',
      h1: 'COMPLETE THE FORM FOR RECEIPT INFORMATION'
    }
  },
  created: function() {
    axios.get('/listOfCountries.json').then(response => {
      this.countries = response.data.countries
    })
  },
  methods: {
    submit () {
        this.$emit('update', {
          country: this.selectedCountry,
          duration: this.picked,
          goal: this.picked2
      })
    }
  }
}
</script>