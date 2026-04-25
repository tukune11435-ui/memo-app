<script setup>
    import DocumentSvg from './svgs/DocumentSvg.vue'
</script>
<template>
        <div class="flex5">
            <div class="flex6 gap-3">
                <DocumentSvg class="w-8 h-8"/>
                <p class="header-color text-4xl font-bold">かんたんメモ</p>
            </div>
            <div class="sec text-gray-600">思いついたことをサッと記録しよう</div>
        </div>
</template>

<style>
.header-color{
    color: #F16E38;
    font-size: 25px;
    font-weight: bold;
}

.flex6{
    display: flex;
    justify-content: center;
    align-items: center;
}
.sec{
    text-align: center;
    font-size: 12px;
}
.flex5{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    box-shadow: 0px 2px 6px rgba(0,0,0,0.05);
    height: 110px;
}
</style>
