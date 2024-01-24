<template>
    <button :style="{background: bgColor, color: color, border: border}">{{text}}</button>
</template>


<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: "ButtonView",
    props: {
        color: {
            type: String, 
            required: true
        },
        bgColor: {
            type: String,
            required: true
        },
        border: {
            type: String
        },
        text: {
            type: String,
            required: true
        }
    }
})
</script>

<style scoped>
button {
    padding: 8px 16px;
    border-radius: 3px;
    cursor: pointer;
    font-weight: 700;
    margin: 0 8px;
}

</style>
