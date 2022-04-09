<template>
  <template v-if="job">
    <h1>{{ job.title }}</h1>
    <p>The job id is {{ id }}</p>
    <p>{{ job.details }}</p>
  </template>


  <div v-else>
    <p>Loading job details...</p>
  </div>
</template>

<script>
  export default {
    name: 'JobDetails',

    props: {
      id: {
        type: String,
        default: '1'
      },
    },

    data() {
      return {
        job: null
      }
    },

    created () {
      fetch(`http://localhost:3000/jobs/${this.id}`)
        .then((res) => res.json())
        .then((data) => this.job = data)
        .catch(err => console.error(err.message))
    },
  }
</script>

<style lang="scss" scoped>

</style>