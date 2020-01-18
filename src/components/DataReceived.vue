<template>
  <div id="DataReceived">
    <h1>{{ h1 }}</h1>
    <div class="data-received">Thank you for your application! We will call you back shortly before {{allData.time}}</div>
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
      h1: 'YOUR INFORMATION HAS BEEN RECEIPT. WE WILL CONTACT YOU'
    }
  }
}
</script>