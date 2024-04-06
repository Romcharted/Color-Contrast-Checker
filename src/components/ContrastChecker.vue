<template>
    <div class="contrast-checker">
        <ContrastCheckerContent
            @textColorChanged="updateTextColor"
            @backgroundColorChanged="updateBackgroundColor"
        />
        <ContrastCheckerPreview
            :textColor="textColor"
            :backgroundColor="backgroundColor"
        />
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import ContrastCheckerContent from "./ContrastCheckerContent.vue";
import ContrastCheckerPreview from "./ContrastCheckerPreview.vue";

let textColor = ref("#FFFFFF");
let backgroundColor = ref("#000000");

const updateTextColor = (newColor: string) => {
    textColor.value = newColor;
};

const updateBackgroundColor = (newColor: string) => {
    backgroundColor.value = newColor;
};
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
