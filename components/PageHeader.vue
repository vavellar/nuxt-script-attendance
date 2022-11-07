<template>
    <div class="header">
        <span>Icone</span>
        <div>Conteúdo a direita</div>
    </div>
</template>

<script>
export default {
    name: 'CopelScriptAttendancePageHeader',

    data() {
        return {
            
        };
    },

    mounted() {
        
    },

    methods: {
        
    },
};
</script>

<style lang="scss" scoped>
.header {
    border-bottom: 1px solid #D7DCF0;
    padding: 1rem;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: 1fr;
    grid-column-gap: 0px;
    grid-row-gap: 0px;

    &__left {
        grid-area: 1 / 1 / 2 / 2;
    }

    &__right {
        grid-area: 1 / 2 / 2 / 3;
    }
}
</style>