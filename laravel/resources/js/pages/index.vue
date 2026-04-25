<script setup lang="ts">
// import Welcome from "../features/Welcome.vue";
    import Header from '../components/Header.vue';
    import Body from '../components/Body.vue';
</script>
<template>
<!--  <Welcome />-->
    <div>
        <Header />
    </div>
    <div class="background-color">
        <Body />
    </div>
</template>
<style>
.background-color{
    background: linear-gradient(
        135deg,
        #f7efe5 0%,
        #f3e7dc 50%,
        #f5e3dc 80%,
        #f6ebe7 100%
    );
    padding-top: 40px;
    padding-bottom: 200px;
    display: flex;
    justify-content: center;
}
</style>
