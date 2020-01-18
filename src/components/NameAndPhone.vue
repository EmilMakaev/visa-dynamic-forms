<template>
  <div id="NameAndPhone">
    <h1>{{ h1 }}</h1>
    <div @input="submit" class="fields">
      <div class="field">
        <label class="label">Your name:</label>
        <div class="control">
          <input 
            v-model="name" 
            class="input" 
            type="text" 
            placeholder="Your name" 
            required
          />
        </div>
      </div>

      <div class="field">
        <label class="label">Your phone:</label>
        <div class="control">
          <input 
            v-model="phone" 
            class="input" 
            type="number" 
            placeholder="Your phone" 
            required
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      h1: 'COMPLETE THE FORM FOR RECEIPT INFORMATION',
      name: '',
      phone: ''
    }
  },
  methods: {
    submit () {
      this.$emit('update', {
        name: this.name,
        phone: this.phone
      })
    }
  }
}
</script>
