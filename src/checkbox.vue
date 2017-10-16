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
        <span class="ks-checkbox__label" v-if="$slots.default || label">
            <slot></slot>
            <template v-if="!$slots.default">{{label}}</template>
        </span>
    </label>
</template>
<style lang="less" scoped>
    @import '~pcadmin-base/src/css/var.less';

    .ks-checkbox {
        user-select: none;

        .ks-checkbox__input {
            font-size: 14px;
            vertical-align: middle;
            cursor: pointer;
            line-height: 1;

            .ks-checkbox__inner {
                top: 1px;
                display: inline-block;
                border: 1px solid #C5C5C5;
                position: relative;
                box-sizing: border-box;
                width: 16px;
                height: 16px;
                border-radius: 4px;
                transition: border-color .25s cubic-bezier(.71, -.46, .29, 1.46), background-color .25s cubic-bezier(.71, -.46, .29, 1.46);
            }

            .ks-checkbox__inner:after {
                content: "";
                border: 2px solid #fff;
                border-left: 0;
                border-top: 0;
                height: 8px;
                left: 4px;
                position: absolute;
                top: 0;
                box-sizing: content-box;
                width: 4px;
                transform: rotate(45deg) scaleY(0);
                transition: transform .15s cubic-bezier(.71, -.46, .88, .6) .05s;
                transform-origin: center;
            }
        }

        .ks-checkbox__input:hover {
            border-color: #1EC773;
        }

        .ks-checkbox__input.is-checked {
            .ks-checkbox__inner {
                background-color: #1EC773;
                border-color: #1EC773;
            }
            .ks-checkbox__inner:after {
                transform: rotate(45deg) scaleY(1);
            }
        }

        .ks-checkbox__input.is-disabled {
            .ks-checkbox__inner {
                background-color: #eef1f6;
                border-color: #d1dbe5;
                cursor: not-allowed;
            }
        }

        .ks-checkbox__input.is-checked.is-disabled {
            .ks-checkbox__inner {
                background-color: #d1dbe5;
                border-color: #d1dbe5;
            }
        }

        .ks-checkbox__label {
            font-size: 14px;
            color: #5E6460;
        }

        .ks-checkbox__input.is-disabled + .ks-checkbox__label {
            color: #bbb;
            cursor: not-allowed;
        }
    }
</style>
<script>
    export default{
        name: 'ksCheckbox',
        componentName: 'ksCheckbox',
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
        watch: {},
        computed: {
            _checkboxGroup() {
                let parent = this.$parent;
                while (parent) {
                    if (parent.$options.componentName !== 'ksCheckboxGroup') {
                        parent = parent.$parent;
                    } else {
                        return parent;
                    }
                }
                return false;
            }
        },
        mounted() {
        },

        methods: {
            handleClick(e) {
                if (this.disabled) {
                    return;
                }
                this.isChecked = !this.isChecked;
                e.checked = this.isChecked;
                this.$emit('change', e);
                let value = this._checkboxGroup.value;
                let index = value.indexOf(this.label);
                if (index > -1) {
                    value.splice(index, 1);
                } else {
                    value.push(this.label);
                }
            }
        },

        created() {
            console.log(this._checkboxGroup.value, this.label);
            let labelList = this._checkboxGroup.value || [];
            if (labelList.indexOf(this.label) > -1) {
                this.isChecked = true;
            }
        }
    };
</script>
