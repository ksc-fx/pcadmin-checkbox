<template>
    <div class="ks-checkbox-group">
        <slot></slot>
    </div>
</template>

<script>
    export default{
        name: 'ksCheckboxGroup',
        componentName: 'ksCheckboxGroup',
        props: {
            value: {}
        }
    };
</script>
