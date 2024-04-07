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

        <Contrast :ratio="ratio" :rate="rate" />
    </div>
</template>

<script setup lang="ts">
import { ref, defineEmits, watch } from "vue";
import InputHexaColor from "./InputHexaColor.vue";
import Contrast from "./Contrast.vue";

const emit = defineEmits(["textColorChanged", "backgroundColorChanged"]);

let textColor = ref("#FFFFFF");
let backgroundColor = ref("#000000");
let ratio = ref(1);
let rate = ref(1);

// Seuils de ratios pour attribuer une note
const ratingThresholds = [3, 4.5, 7, 12, 999];

const calculateContrastRatio = (hexColor1: string, hexColor2: string) => {
    const luminance1 = calculateLuminance(hexColor1);
    const luminance2 = calculateLuminance(hexColor2);
    const contrastRatio =
        (Math.max(luminance1, luminance2) + 0.05) /
        (Math.min(luminance1, luminance2) + 0.05);
    return Number(contrastRatio.toFixed(2));
};

const calculateLuminance = (hexColor: string) => {
    const r = parseInt(hexColor.substring(1, 3), 16) / 255;
    const g = parseInt(hexColor.substring(3, 5), 16) / 255;
    const b = parseInt(hexColor.substring(5, 7), 16) / 255;
    return 0.2126 * r + 0.7152 * g + 0.0722 * b;
};

const changeContrast = () => {
    ratio.value = calculateContrastRatio(
        textColor.value,
        backgroundColor.value
    );

    // Attribution de la note en fonction du ratio calculé et des seuils définis
    for (let i = 0; i < ratingThresholds.length; i++) {
        if (ratio.value < ratingThresholds[i]) {
            rate.value = i + 1;
            break;
        }
    }
};

// Mise à jour du ratio et du score lorsque textColor ou backgroundColor change
watch([textColor, backgroundColor], () => {
    changeContrast();
});

changeContrast();

const updateTextColor = (newColor: string) => {
    textColor.value = newColor;
    emit("textColorChanged", newColor);
};

const updateBackgroundColor = (newColor: string) => {
    backgroundColor.value = newColor;
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
    gap: 24px;
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
        border-radius: 0px 0 14px 14px;
    }
}

@media screen and (max-width: 464px) {
    .input-container {
        flex-direction: column;
    }
}
</style>
