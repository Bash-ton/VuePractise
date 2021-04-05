<template>
  <h1>{{ jobInfo?.title }}</h1>
  <p>The job id is {{ id }}</p>
  <p>This is the description: {{ jobInfo?.details }}</p>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      jobInfo: null
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.jobInfo = data))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
</style>