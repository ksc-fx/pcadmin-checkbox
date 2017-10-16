<template>
    <div>
        <div>
            <ks-checkbox-group v-model="checklist">
                <ks-Checkbox @change="onChange" label="默认复选框"></ks-Checkbox>
                <ks-Checkbox @change="onChange" label="默认勾选"></ks-Checkbox>
            </ks-checkbox-group>
        </div>
        <div>
            <ks-Checkbox disabled @change="onChange" label="不可用"></ks-Checkbox>
            <ks-Checkbox checked disabled @change="onChange" label="勾选不可用"></ks-Checkbox>
        </div>
    </div>
</template>

<style lang="less">
</style>

<script>
    import ksCheckboxGroup from '../src/checkbox-group.vue';
    import ksCheckbox from '../src/checkbox.vue';

    export default {
        data () {
            return {
                checklist: ['默认复选框']
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
            ksCheckboxGroup,
            ksCheckbox
        }
    };
</script>

