<template>
    <label class="ks-checkbox" @click="handleClick">
        <span class="ks-checkbox__input"
              :class="{
            'is-disabled': disabled,
            'is-checked': isChecked,
            'is-indeterminate': indeterminate
            }"
        >
            <span class="ks-checkbox__inner"></span>
        </span>
        <span class="ks-checkbox__label"><slot></slot></span>
    </label>
</template>
<style lang="less" scoped>
    @import '~pcadmin-base/src/css/var.less';

    .ks-checkbox {

        .ks-checkbox__input {
            font-size: 14px;
            vertical-align: middle;
            cursor: pointer;
            line-height: 1;
            position: relative;
            display: inline-block;
            width: 16px;
            height: 16px;
            border: 1px solid #C5C5C5;
            border-radius: 4px;

            .ks-checkbox__inner {
                border: 2px solid #fff;
                border-left: 0;
                border-top: 0;
                height: 8px;
                left: 5px;
                position: absolute;
                top: 2px;
                width: 4px;
                transform: rotate(45deg);
            }
        }

        .ks-checkbox__input.is-checked {
            background-color: #1EC773;
            border-color: #1EC773;
        }

        .ks-checkbox__label {
            font-size: 14px;
            color: #5E6460;
        }
    }
</style>
<script>
    export default{
        name: 'checkbox',
        props: {
            disabled: Boolean,
            checked: {
                type: Boolean,
                default: false
            },
            indeterminate: Boolean,
            label: {}
        },
        data() {
            return {
                isChecked: this.checked
            };
        },
        watch: {
            checked(checked) {
                this.isChecked = checked;
            }
        },
        computed: {

        },
        mounted() {
        },

        methods: {
            handleClick(e) {
                this.isChecked = !this.isChecked;
                e.checked = this.isChecked;
                this.$emit('change', e);
            }
        }
    };
</script>
