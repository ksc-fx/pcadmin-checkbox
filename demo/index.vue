<template>
    <div>
        <ksCheckbox checked disabled @change="onChange">默认复选框</ksCheckbox>
    </div>
</template>

<style lang="less">
</style>

<script>
    import ksCheckbox from '../src/checkbox.vue';

    export default {
        data () {
            return {

            };
        },
        mounted () {
        },
        methods: {
            onChange(e) {
                console.log('checked:', e.checked);
            }
        },
        components: {
            ksCheckbox
        }
    };
</script>

