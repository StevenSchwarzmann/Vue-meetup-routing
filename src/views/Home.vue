<template>
  <div class="home">
    <ul>
      <li v-for="project in projects" :key="project.id">
       <router-link :to="'/' + project.id">{{ project.title }} </router-link>
       </li>
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  data: () => ({
    projects: null
  }),

  async created() {
    const url = `https://jsonplaceholder.typicode.com/posts/`
    //const url = `https://api.github.com/users/sdvue/repos`
    this.projects = await fetch(url).then(res => res.json())
  }
};
</script>
