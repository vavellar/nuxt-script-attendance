<template>
    <div>
        <div class="py-2" v-for="content in service.content" :key="content.title">
            <h1 class="text-2xl">{{ content.title }}</h1>
            <div class="p-2" v-for="content in getContent(content.description)">
                    <span>
                        {{ content.replace('-', '&bull;') }}
                    </span>
                </div>

            <div v-for="instruction in content.instructions" :key="instruction.title">
                <h1 class="text-2xl py-3">
                    {{ instruction.title}}
                </h1>
                <div class="p-2" v-for="content in getContent(instruction.description)">
                    <span>
                        {{ content.replace('-', '&bull;') }}
                    </span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        service: { type: Object}
    },
    name: 'CopelScriptAttendancePageContent',

    methods: {
      getContent(description) {
        return description.split('\n')
      }
    }
};
</script>

<style lang="scss" scoped>

</style>