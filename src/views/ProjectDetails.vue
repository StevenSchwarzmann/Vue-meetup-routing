<template>
  <div class="project">
    <template v-if="details">
      <h3> {{ details.title }} </h3>
      <p>
        <strong> By: {{ details.userId }} </strong>
      </p>
      <p> {{ details.body }} </p>
    </template>
    <router-link to="/">Home</router-link>
  </div>
</template>

<script>
export default {
  props: ['id'],
  
  data: () => ({
    details: null
  }),
  async created() {
    //const name = this.$route.params.name;
    //const url = `https://api.github.com/repos/sdvue/${name}`
    console.log('id', this.id)
    const url = `https://jsonplaceholder.typicode.com/posts/${this.id}`
    this.details = await fetch(url).then(res => res.json())
  }
};
</script>