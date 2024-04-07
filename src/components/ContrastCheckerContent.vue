<template>
    <div class="contrast-checker-content">
        <div class="input-container">
            <InputHexaColor
                title="Text Color"
                defaultValue="#FFFFFF"
                @colorChanged="updateTextColor"
            />
            <InputHexaColor
                title="Background Color"
                defaultValue="#000000"
                @colorChanged="updateBackgroundColor"
            />
        </div>

        <Contrast :rate="4" />
    </div>
</template>

<script setup lang="ts">
import { defineEmits } from "vue";
import InputHexaColor from "./InputHexaColor.vue";
import Contrast from "./Contrast.vue";

const emit = defineEmits(["textColorChanged", "backgroundColorChanged"]);

const updateTextColor = (newColor: string) => {
    emit("textColorChanged", newColor);
};

const updateBackgroundColor = (newColor: string) => {
    emit("backgroundColorChanged", newColor);
};
</script>

<style>
.contrast-checker-content {
    width: 50%;
    padding: 30px;
    display: flex;
    flex-direction: column;
    align-items: stretch;
    justify-content: flex-start;
    background-color: var(--background-color);
    box-shadow: inset rgba(0, 0, 0, 0.11) 0 0 0 1px;
    border-radius: 14px 0 0 14px; /* Sinon bordure coupé */
    min-width: 350px;
}

.input-container {
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 24px;
}

@media screen and (max-width: 764px) {
    .contrast-checker-content {
        width: 100%;
    }
}
</style>
