<script setup>
const modelValue = defineModel()
</script>
<template>
    <textarea
        rows="5" cols="73"
        class="outline-none focus:border-blue-400 border rounded-md"
        v-model="modelValue"
        placeholder="メモを入力してください...
（Enterで保存、Shift+Enterで改行）"
    >
    </textarea>
</template>
