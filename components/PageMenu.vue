<template>
    <div class="menu">
        <NuxtLink :to="item.route"  v-for="item in menuItems" :key="item.name" class="menu__item">
            {{ item.name}}
        </NuxtLink>
        
    </div>
</template>

<script>
import GetMenu from '@/apollo/queries/menu.gql'
export default {
    data() {
        return {
            menu: {}
        }
    },

    apollo: {
        menu: {
            prefetch: true,
            query: GetMenu,
        },
    },

    computed: {
        menuItems() {
            return this.menu.data.attributes.item
        },
    }

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