<template>
    <div :style="{backgroundColor: color }" class="btn">
        Apple
    </div>
</template>

<script>
    export default {
        props: {
            color: {
                type: String,
                default: 'gray'
            }
        }

}
</script>

<style scoped>
    .btn {
        display: inline-block;
        margin: 4px;
        padding: 6px 12px;
        border-radius: 4px;
        background-color: gray;
        color: white;
        cursor: pointer;
    }
</style>