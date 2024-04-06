<template>
    <div class="contrast-checker-content">
        <InputHexaColor />
        <InputHexaColor />
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import InputHexaColor from "./InputHexaColor.vue";
</script>

<style>
.contrast-checker-content {
    width: 50%;
    height: 100%;
    padding: 30px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: var(--background-color);
    box-shadow: inset rgba(0, 0, 0, 0.11) 0 0 0 1px;
    border-radius: 14px 0 0 14px; /* Sinon bordure coupé */
    min-width: 350px;
}

@media screen and (max-width: 764px) {
    .contrast-checker-content {
        width: 100%;
    }
}
</style>
