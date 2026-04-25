<script setup>
    import PlusSvg from "@/components/svgs/PlusSvg.vue";
    import TextareaForm from "@/components/TextareaForm.vue";
    import Button from "@/components/Button.vue";
    import TrashSvg from "@/components/svgs/TrashSvg.vue";

    import {ref,onMounted} from 'vue'
    import DocumentSvg from "@/components/svgs/DocumentSvg.vue";

    const memoContent = ref('')
    const memos = ref([])
    import axios from 'axios'

    const fetchMemos = async () => {
        const res = await axios.get('/api/memos')
        memos.value = res.data
    }
    const saveMemo = async () => {
        const res = await axios.post('/api/memos', {content: memoContent.value})
        memos.value.unshift(res.data)
        memoContent.value = ''
    }
    onMounted(() => {
        fetchMemos()
    })

    const formatDate = (dateString) => {
        const date = new Date(dateString)

        return date.toLocaleString('ja-JP', {
            year: 'numeric',
            month: '2-digit',
            day: '2-digit',
            hour: '2-digit',
            minute: '2-digit',
        })
    }

</script>
<template>
    <div class="memo-wrapper">
        <div class="flex1">
            <div class="flex3 items-center">　
                <PlusSvg />
                <p class="font-semibold">新しいメモ</p>
            </div>
            <div class="flex4 gap-4">
                <div>
                    <TextareaForm v-model="memoContent" @keydown.enter.exact.prevent="saveMemo"/>
                </div>
                <div>
                    <Button v-model="memoContent" @click="saveMemo"/>
                </div>

            </div>
        </div>

        <div class="gap-4">
            <div class="saved-memo-header">
                <div class="flex gap-2 mb-4 items-center">
                    <DocumentSvg />
                    <p class="font-semibold">保存されたメモ</p>
                </div>
                <div class="memo-count">{{ memos.length }}件</div>
            </div>
            <div class="saved-memo group" v-for="memo in memos" :key="memo.id">
                <div class="flex items-center justify-between">
                    <p>{{ memo.content }}</p>
                    <TrashSvg class="opacity-0 group-hover:opacity-100 transition-opacity duration-200"/>
                </div>
                <p class="memo-date mt-2">{{ formatDate(memo.created_at) }}</p>
            </div>
        </div>
    </div>
</template>
<style>
 .flex1 {
     border: 1px solid #ccc;
     box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.1);
     border-radius: 10px;
     padding: 30px 15px 30px 15px;
     background-color: white;
     width: 700px;
 }
 .flex3{
     display: flex;
     align-items: center;
     gap: 8px;
     margin-bottom: 15px;
 }
 .flex4{
     display: flex;
     flex-direction: column;
     justify-content: center;
     align-items: center;
 }
 .memo-wrapper {
     display: flex;
     flex-direction: column;
     gap: 35px;
 }
 .saved-memo{
     border: 1px solid #ccc;
     box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.1);
     border-radius: 10px;
     background-color: white;
     padding: 30px;
     margin-bottom: 15px;
 }
 .memo-date{
     font-size: 10px;
     color: #94a3b8;
 }
 .memo-count{
     background-color: #fff0d9;
     color: #6b7280;
     padding: 3px 10px;
     border-radius: 999px;
     font-size: 13px;
 }
 .saved-memo-header {
     display: flex;
     justify-content: space-between;
     align-items: center;
     margin-bottom: 24px;
 }
</style>
