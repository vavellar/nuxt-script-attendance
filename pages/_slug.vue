<template>
  <div class="indexPage">
    <pre>
      {{ service}}
    </pre>
    <h1 class="indexPage__title">
      {{ service.data.attributes.service_name}}
    </h1>

    <h1>
      {{ service.data.attributes.concept.field_title}}
    </h1>
    <h3>
      {{ service.data.attributes.concept.field_description}}
    </h3>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      service: null
    }
  },
  async asyncData({ params, $axios }) {
      const service = await $axios.$get(`http://localhost:1337/api/servicos/${params.slug}?populate=*`)
      return { service }
    }
}
</script>

<style lang="scss" scoped>
.indexPage {
  padding: 20px;
}
</style>
