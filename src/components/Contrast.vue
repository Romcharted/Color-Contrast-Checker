<template>
    <div class="contrast-container" :data-rating="rate">
        <MainContrastView ratio="1" textRate="Very Poor" :rate="rate" />
    </div>
</template>

<script setup lang="ts">
import MainContrastView from "./MainContrastView.vue";

const props = defineProps({
    rate: Number || 1,
});
</script>

<style>
.contrast-container {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
    border-radius: 10px;
    overflow: hidden;
}

/* =================================== CSS Color Rate =================================== */
.contrast-container[data-rating="1"] .main-contrast-view,
.contrast-container[data-rating="2"] .main-contrast-view {
    background: var(--background-rate-level-1);
    color: var(--text-rate-level-1);
}

.contrast-container[data-rating="3"] .main-contrast-view {
    background: var(--background-rate-level-2);
    color: var(--text-rate-level-2);
}

.contrast-container[data-rating="4"] .main-contrast-view,
.contrast-container[data-rating="5"] .main-contrast-view {
    background-color: var(--background-rate-level-3);
    color: var(--text-rate-level-3);
}
</style>
