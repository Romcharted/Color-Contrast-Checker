<template>
    <div class="contrast-text-rate">
        <span>{{ value }}</span>
    </div>
</template>

<script setup lang="ts">
const props = defineProps({
    value: String,
});
</script>

<style>
.contrast-text-rate {
}
</style>
