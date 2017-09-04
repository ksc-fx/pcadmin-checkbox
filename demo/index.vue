<template>
    <div>
        <checkbox @change="onChange">默认按钮</checkbox>
    </div>
</template>

<style lang="less">
</style>

<script>
    import checkbox from '../src/checkbox.vue';

    export default {
        data () {
            return {};
        },
        mounted () {
        },
        methods: {
            onChange(e) {
                console.log('checked:', e.checked);
            }
        },
        components: {
            checkbox
        }
    };
</script>

