<template>
  <h1>
    Jobs
  </h1>
  <template v-if="jobs.length">
    <div v-for="job in jobs" :key="job.id" class="job">
      <router-link :to="{ name: 'JobDetails', params: { id: job.id } }">
        <h2>{{ job.title }}</h2>
      </router-link>
    </div>
  </template>

  <div v-else>
    <p>Loading jobs...</p>
  </div>
</template>

<script>
  export default {
    name: 'Jobs',

    data() {
      return {
        jobs: []
      }
    },

    created() {
      fetch('http://localhost:3000/jobs')
        .then((res) => res.json())
        .then((data) => this.jobs = data)
        .catch(err => console.error(err.message))
    }
  }
</script>

<style lang="scss" scoped>
.job {
  h2 {
    background-color: #f4f4f4;
    padding: 20px;
    border-radius: 10px;
    margin: 10px auto;
    max-width: 600px;
    cursor: pointer;
    color: #444;

    &:hover {
      background-color: #ddd;
    }
  }

  a {
    text-decoration: none;
  }
}
</style>