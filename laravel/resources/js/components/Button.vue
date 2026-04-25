<script setup>
    import PlusSvg from "@/components/svgs/PlusSvg.vue";
    const memoContent = defineModel();
    const emit = defineEmits(['click']);
</script>
<template>
    <button class="flex2 white border rounded-md" @click="emit('click')" :disabled="!memoContent" :class=" memoContent ? 'bg-[#F16E38] text-white' : 'bg-[#F16E38] text-white opacity-50 cursor-not-allowed'">
        <PlusSvg class="white"/>
        メモを保存
    </button>
</template>
<style>
.flex2{
    display: flex;
    border: 1px solid #ccc;
    background: linear-gradient(to right, #f97316, #ef4444);
    padding: 10px 250px 10px 250px;
    text-align: center;
    justify-content: center;
    gap: 8px;
    align-items: center;
}
.white{
    color: white;
}
</style>
