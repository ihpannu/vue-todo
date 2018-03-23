<template>
  <div class="about">
      <h1>Hello {{ their_name }}, this is an about page</h1>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis repellat recusandae adipisci dolorem molestiae vitae facere hic laboriosam sint delectus! Ullam exercitationem incidunt officiis eveniet odit laborum obcaecati quas debitis.</p>
  </div>
</template>
<script>
export default {
  name: 'Skills',
  data() {
    return {
      their_name: this.$route.params.name
    };
  }
};
</script>
