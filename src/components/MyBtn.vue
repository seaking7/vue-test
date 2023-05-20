<template>
    <div :style="{backgroundColor: color }"
    :class="{ large }" class="btn">
    <slot name="icon">(a)</slot>
    <slot name="text">Fallback</slot>
    </div>
    <h5 @dblclick="$emit('myEvent', $event)">ABC</h5>
    <input type="text" v-model="msg" />
</template>

<script>
export default {
    inheritAttrs: false,
    emits: [
        'myEvent',
        'changeMsg'
    ],
    data() {
        return {
            msg: ''
        }
    },
    watch: {
        msg() {
            this.$emit('changeMsg', this.msg)
        }
    },
    props: {
        color: {
            type: String,
            default: 'gray'
        },
        large: {
            type: Boolean,
            default: false
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
    .btn.large {
        font-size: 20px;
        padding: 10px 20px;
    }
</style>