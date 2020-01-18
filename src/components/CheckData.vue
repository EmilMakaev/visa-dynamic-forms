<template>
  <div id="CheckData">
    <h1>{{ h1 }}</h1>
    <div class="check-data">
      <div>
        <p><span class="description">Country:</span> {{ allData.country }}</p>  
        <p><span class="description">Duration:</span> {{ allData.duration }}</p>
        <p><span class="description">Goal:</span> {{ allData.goal }}</p>
        <p><span class="description">Name:</span> {{ allData.name }}</p>
        <p><span class="description">Phone:</span> {{ allData.phone }}</p>
      </div>

      <div @change="submit">
        <p class="description">When to call you?</p>
        <div>
          <input 
            type="radio" 
            id="one" 
            value="Until 12:00" 
            v-model="time"
          >
          <label for="one">Until 12:00</label>
        </div>
        <div>
          <input 
            type="radio" 
            id="two" 
            value="Until 15:00" 
            v-model="time"
          >
          <label for="two">Until 15:00</label>
        </div>
        <div>
          <input 
            type="radio" 
            id="three" 
            value="Until 18:00" 
            v-model="time"
          >
          <label for="three">Until 18:00</label>
        </div>
        <div>
          <input 
            type="radio" 
            id="four" 
            value="Until 21:00" 
            v-model="time"
          >
          <label for="four">Until 21:00</label>
        </div>
      </div>
    </div>   
  </div>
</template>

<script>
export default {
  props: {
    allData: {
      type: Object,
      required: true
    }
  },
  data () {
    return {
      h1: 'CHECK YOUR INFORMATION AND CLICK NEXT',
      form: '',
      time: ''
    }
  },
  methods: {
    submit () {
        this.$emit('update', {
          time: this.time
      })
    }
  }
}
</script>