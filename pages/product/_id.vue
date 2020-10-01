<template>
  <div style="text-align : center">
    <a :href="$route.params.data.url">
      <img
        :src="this.$route.params.data.image_url"
        alt=""
      >
    </a>
    <h1>
      {{ this.$route.params.data.title }}
    </h1>
    <h2>
      {{ this.$route.params.data.synopsis }}
    </h2>
    <br>
    <br>
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
