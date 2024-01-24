<template>
    <h1>{{title}}</h1>
</template>

<script lang="ts">
import { defineComponent, PropType} from "vue"
export default defineComponent({
name: "TitleView",
props: {
    title: {
        type: String as PropType<string>,
        required: true
    }
}
})
</script>