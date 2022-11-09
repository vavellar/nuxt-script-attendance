<template>
  <div class="indexPage">

      <h1 class="indexPage__title">
        {{ service.data.attributes.service_name}}
      </h1>
    
    <div v-for="item in service.data.attributes.content" class="indexPage__item">
      <h1 class="indexPage__item__title">
        {{ item.title }}
      </h1>

      <div v-for="content in getContent(item.description)">
        <span>{{ content }}</span>
      </div>
    </div>

    <pre>
      {{ service}}
    </pre>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({ params, $axios }) {
    const service = await $axios.$get(`http://localhost:1337/api/servicos/${params.slug}?populate=*`)
    return { service }
  },

  methods: {
    getContent(description) {
      return description.split('\n')
    }
  }
}
</script>

<style lang="scss" scoped>
.indexPage {
  padding: 20px;

  &__title {
    font-size: 32px;
  }

  &__item {
    padding: 20px 0;

    &__title {
      font-size: 24px;
      padding-bottom: 20px;
    }
  }
}
</style>
