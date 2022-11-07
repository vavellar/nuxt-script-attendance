<template>
    <div class="menu">
        <span v-if="$fetchState.pending">Carregando</span>
        <p v-else-if="$fetchState.error">An error occurred :(</p>
        <p v-if="isLoading"> Loading..</p>
        <NuxtLink v-else :to="item.route"  v-for="item in menuItems" :key="item.name" class="menu__item">
            {{ item.name}}
        </NuxtLink>
    </div>
</template>

<script>

export default {
    name: 'CopelScriptAttendancePageMenu',

    data() {
        return {
            menuItems: null,
        };
    },

    async fetch() {
      const response = await fetch(
        'http://localhost:1337/api/menu?populate=*'
      ).then(res => res.json())

      this.menuItems = response.data.attributes.item
    },

};
</script>

<style lang="scss" scoped>
.menu {
    display: flex;
    flex-direction: column;
    height: 100%;
    border-right: 1px solid #D7DCF0;
    padding: 10px;

    &__item {
        padding: 10px;
        text-decoration: none;
        color: #535B76;
        &:hover {
            background-color: #92afe986;
            border-radius: 4px;
        }
    }
}
</style>