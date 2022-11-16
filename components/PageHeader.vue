<template>
    <div class="header">
        <img width="194" height="32" svg-inline src="../assets/icons/somus-logo.svg" />
        <div class="header__content">
            <SearchInput label="Pesquisa Rápida"/>
        </div>
    </div>
</template>

<script>
import SearchInput from './SearchInput.vue';

export default {
    name: "CopelScriptAttendancePageHeader",
    data() {
        return {};
    },
    mounted() {
    },
    methods: {},
    components: { SearchInput }
};
</script>

<style lang="scss" scoped>
.header {
    border-bottom: 1px solid #D7DCF0;
    padding: 1rem;
    align-items: center;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: 1fr;
    grid-column-gap: 0px;
    grid-row-gap: 0px;
}
</style>