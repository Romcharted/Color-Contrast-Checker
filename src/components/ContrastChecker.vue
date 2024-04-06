<template>
    <div class="contrast-checker">
        <ContrastCheckerContent />
        <ContrastCheckerPreview textColor="#112A46" backgroundColor="#ACC8E5" />
    </div>
</template>

<script setup lang="ts">
import ContrastCheckerContent from "./ContrastCheckerContent.vue";
import ContrastCheckerPreview from "./ContrastCheckerPreview.vue";
</script>

<style>
.contrast-checker {
    border-radius: 14px;
    overflow: hidden;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    margin: 100px 0;
    width: 100%;
    max-width: 1200px;
}

@media screen and (max-width: 764px) {
    .contrast-checker {
        flex-direction: column-reverse;
    }
}
</style>
