<template>
    <div
        class="contrast-checker-preview"
        :style="{ backgroundColor: backgroundColor, color: textColor }"
    >
        <span class="preview-title">Preview</span>
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Cumque
            officiis officia commodi earum totam ipsam, pariatur nisi,
            repellendus cum aperiam fugiat libero non! Maxime, dolore cupiditate
            quidem id quibusdam voluptatum.
        </p>
        <span class="small-text">Small Texte (max 18px)</span>
        <span class="small-text-bold"><b>Small Texte Bold (max 14px)</b></span>
    </div>
</template>

<script setup lang="ts">
defineProps({
    textColor: String,
    backgroundColor: String,
});
</script>

<style>
.contrast-checker-preview {
    width: 50%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 30px;
    padding: 50px;
}

.preview-title {
    font-size: 36px;
}

.contrast-checker-preview p {
    text-align: center;
}

.small-text {
    font-size: 18px;
}

.small-text-bold {
    font-size: 14px;
}

@media screen and (max-width: 764px) {
    .contrast-checker-preview {
        width: 100%;
    }
}
</style>
