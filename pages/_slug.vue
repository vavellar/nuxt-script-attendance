<template>
  <div class="indexPage" v-if="service">
    <h1 class="indexPage__title">
      {{ service.service_name}}
    </h1>
    <PageContent :service="service"/>
    <v-divider class="my-10" />
    <footer class="indexPage__footer">
      <div class="indexPage__footer__item">
        <div class="flex p-2 text-blue-600 hover:bg-blue-200 rounded"  v-if="currentService.previousItem">
          <img class="pr-2" src="../assets/icons/arrow-left.svg" alt="">
          <NuxtLink 
            :to="currentService.previousItem.route"
          >
            {{ currentService.previousItem.name}}
          </NuxtLink>
        </div>
        <div class="flex p-2 text-blue-600 hover:bg-blue-200 rounded"  v-if="currentService.nextItem">
          <NuxtLink 
            :to="currentService.nextItem.route"
          >
            {{ currentService.nextItem.name }}
          </NuxtLink>
          <img class="pl-2" src="../assets/icons/arrow-right.svg" alt="">
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import GetService from '@/apollo/queries/service.gql'
import GetMenu from '@/apollo/queries/menu.gql'
import PageContent from '~/components/PageContent.vue';
export default {
    name: "IndexPage",
    components: { PageContent },
    data() {
        return {
            servicos: {},
            menu: {}
        };
    },
    apollo: {
      servicos: {
          prefetch: true,
          query: GetService,
          variables() {
              return { slug: this.$route.params.slug };
          },
      },
      menu: {
          prefetch: true,
          query: GetMenu,
      },
    },
    computed: {
        service() {
            return this.servicos.data && this.servicos.data[0].attributes;
        },

        menuItems() {
          return this.menu.data.attributes.item
        },

        currentService() {
          const currentService = this.menuItems.findIndex((item) => item.route === this.$route.params.slug)
          const isLastItem = currentService === this.menuItems.length - 1
          const isFirsItem = currentService === 0
          const nextItem = isLastItem ? null : this.menuItems[currentService + 1]
          const previousItem = isFirsItem ? null : this.menuItems[currentService - 1]
          return {
              nextItem,
              previousItem
          }
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

  &__footer {
    &__item {
      display: flex;
      justify-content: space-between;
    }
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
