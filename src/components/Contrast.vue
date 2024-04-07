<template>
    <div class="contrast" :data-rating="rate">
        <span class="contrast-title">Contrast</span>

        <div class="contrast-container" v-if="rate">
            <MainContrastView
                :ratio="ratio"
                :textRate="textRate[rate - 1]"
                :rate="rate"
            />
            <div class="contrast-text-rate-container">
                <ContrastTextRate
                    name="Small text"
                    id="small-text"
                    :numberActiveStar="smallTextActiveStar"
                />
                <ContrastTextRate
                    name="Large text"
                    id="large-text"
                    :numberActiveStar="largeTextActiveStar"
                />
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, watch } from "vue";
import MainContrastView from "./MainContrastView.vue";
import ContrastTextRate from "./ContrastTextRate.vue";

const props = defineProps({
    rate: Number,
    ratio: Number,
});

let smallTextActiveStar = ref(1);
let largeTextActiveStar = ref(1);
let textRate = ["Very Poor", "Poor", "Good", "Very Good", "Super"];

watch(
    () => props.rate,
    (newRate) => {
        if (!newRate) {
            return;
        }

        if (newRate >= 4 && newRate <= 5) {
            smallTextActiveStar.value = 3;
        } else if (newRate >= 3) {
            smallTextActiveStar.value = 2;
        } else {
            smallTextActiveStar.value = 1;
        }

        if (newRate >= 3 && newRate <= 5) {
            largeTextActiveStar.value = 3;
        } else if (newRate >= 2) {
            largeTextActiveStar.value = 2;
        } else {
            largeTextActiveStar.value = 1;
        }
    }
);
</script>

<style>
.contrast {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
}

.contrast-container {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
    border-radius: 10px;
    overflow: hidden;
}

.contrast-title {
    font-size: 14px;
    padding-bottom: 14px;
    font-weight: 500;
}

.contrast-text-rate-container {
    display: flex;
    width: 100%;
}

/* =================================== CSS Color Rate =================================== */

/* === main-contrast-view === */
.contrast[data-rating="1"] .main-contrast-view,
.contrast[data-rating="2"] .main-contrast-view {
    background: var(--background-rate-level-1);
    color: var(--text-rate-level-1);
}

.contrast[data-rating="3"] .main-contrast-view {
    background: var(--background-rate-level-2);
    color: var(--text-rate-level-2);
}

.contrast[data-rating="4"] .main-contrast-view,
.contrast[data-rating="5"] .main-contrast-view {
    background-color: var(--background-rate-level-3);
    color: var(--text-rate-level-3);
}

/* === small-text=== */
.contrast[data-rating="1"] #small-text,
.contrast[data-rating="2"] #small-text {
    background: var(--background-rate-level-1);
    color: var(--text-rate-level-1);
}

.contrast[data-rating="3"] #small-text {
    background: var(--background-rate-level-2);
    color: var(--text-rate-level-2);
}

.contrast[data-rating="4"] #small-text,
.contrast[data-rating="5"] #small-text {
    background-color: var(--background-rate-level-3);
    color: var(--text-rate-level-3);
}

/* STAR */
.contrast[data-rating="1"] #small-text .rating-star svg,
.contrast[data-rating="2"] #small-text .rating-star svg {
    fill: var(--text-rate-level-1);
}

.contrast[data-rating="3"] #small-text .rating-star svg {
    fill: var(--text-rate-level-2);
}

.contrast[data-rating="4"] #small-text .rating-star svg,
.contrast[data-rating="5"] #small-text .rating-star svg {
    fill: var(--text-rate-level-3);
}

/* === large-text=== */
.contrast[data-rating="1"] #large-text {
    background: var(--background-rate-level-1);
    color: var(--text-rate-level-1);
}

.contrast[data-rating="2"] #large-text {
    background: var(--background-rate-level-2);
    color: var(--text-rate-level-2);
}

.contrast[data-rating="3"] #large-text,
.contrast[data-rating="4"] #large-text,
.contrast[data-rating="5"] #large-text {
    background-color: var(--background-rate-level-3);
    color: var(--text-rate-level-3);
}

/* STAR */
.contrast[data-rating="1"] #large-text .rating-star svg {
    fill: var(--text-rate-level-1);
}

.contrast[data-rating="2"] #large-text .rating-star svg {
    fill: var(--text-rate-level-2);
}

.contrast[data-rating="3"] #large-text .rating-star svg,
.contrast[data-rating="4"] #large-text .rating-star svg,
.contrast[data-rating="5"] #large-text .rating-star svg {
    fill: var(--text-rate-level-3);
}
</style>
