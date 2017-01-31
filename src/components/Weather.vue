<template>
  <div class="weather">
    <div class="location">{{location}}</div>
    <div class="date">{{date}}</div>
    <div class="description">{{description}}</div>
  </div>
</template>

<script>
export default {
  name: 'weather',
  data () {
    return {
      location: 'New York, NY',
      date: 'Tuesday, April 15th',
      description: 'desc here'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
