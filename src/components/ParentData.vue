<template>
    <ChildData :msg="msg" />
</template>

<script>
import ChildData from './ChildData.vue'

export default {
    components: {
        ChildData
    },
    props: {
        msg: {
            type: String,
            default: ''
        }
    }
}

</script>