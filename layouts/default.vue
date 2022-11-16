<template>
  <section class="page">
    <section class="page__header">
      <PageHeader />
    </section>
    <section class="page__content">
      <aside class="page__content__aside">
        <PageMenu />
      </aside>
      <main class="page__content__center">
        <v-container>
          <Nuxt />
        </v-container>
      </main>
      <div class="page__content__progress">
        <PageProgress />
      </div>
    </section>
  </section>
</template>

<script>
import PageHeader from '~/components/PageHeader.vue';
import PageMenu from '~/components/PageMenu.vue';
import PageProgress from '~/components/PageProgress.vue';
export default {
  name: "DefaultLayout",
  components: { PageHeader, PageMenu, PageProgress },
}
</script>

<style lang="scss" scoped>
.page {
  height: 100vh;
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 0.1fr;

  &__header {
    grid-area: 1 / 1 / 2 / 2;
  }

  &__content {
    grid-area: 2 / 1 / 3 / 2;
    display: grid;
    overflow-x: auto;
    grid-template-columns: 0.4fr 1fr 0.4fr;
    grid-template-rows: 1fr;
    grid-column-gap: 0px;
    grid-row-gap: 0px;

    &__aside {
      grid-area: 1 / 1 / 2 / 2;
    }

    &__center {
      overflow: auto;
      grid-area: 1 / 2 / 2 / 3;
    }

    &__progress {
      grid-area: 1 / 3 / 2 / 4; 
    }
  }
}
</style>
