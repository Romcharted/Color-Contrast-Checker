<template>
    <div class="main-contrast-view">
        <span class="main-contrast-value">{{ ratio }}</span>
        <div class="main-contrast-rating">
            <span>{{ textRate }}</span>
            <div class="contrast-rate-star-container" v-if="rate">
                <div
                    class="rating-star"
                    v-for="index in 5"
                    :key="index"
                    :class="{ active: index <= rate }"
                >
                    <svg
                        xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 576 512"
                    >
                        <!-- Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.  -->
                        <path
                            d="M316.9 18C311.6 7 300.4 0 288.1 0s-23.4 7-28.8 18L195 150.3 51.4 171.5c-12 1.8-22 10.2-25.7 21.7s-.7 24.2 7.9 32.7L137.8 329 113.2 474.7c-2 12 3 24.2 12.9 31.3s23 8 33.8 2.3l128.3-68.5 128.3 68.5c10.8 5.7 23.9 4.9 33.8-2.3s14.9-19.3 12.9-31.3L438.5 329 542.7 225.9c8.6-8.5 11.7-21.2 7.9-32.7s-13.7-19.9-25.7-21.7L381.2 150.3 316.9 18z"
                        />
                    </svg>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
const props = defineProps({
    ratio: Number,
    textRate: String,
    rate: Number,
});
</script>

<style>
.main-contrast-view {
    display: flex;
    padding: 30px;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 2px;
}

.main-contrast-value {
    font-size: 50px;
    font-weight: 700;
}

.main-contrast-rating {
    display: flex;
    flex-direction: column;
    gap: 10px;
}
.main-contrast-rating span {
    font-size: 16px;
    font-weight: 600;
    text-align: center;
}

.contrast-rate-star-container {
    display: flex;
    align-items: center;
    gap: 5px;
    justify-content: center;
}

.rating-star {
    width: 18px;
    height: 18px;
    opacity: 0.5;
}

.rating-star.active {
    opacity: 1;
}

.contrast[data-rating="1"] .main-contrast-view .rating-star svg,
.contrast[data-rating="2"] .main-contrast-view .rating-star svg {
    fill: var(--text-rate-level-1);
}

.contrast[data-rating="3"] .main-contrast-view .rating-star svg {
    fill: var(--text-rate-level-2);
}

.contrast[data-rating="4"] .main-contrast-view rating-star svg,
.contrast[data-rating="5"] .main-contrast-view .rating-star svg {
    fill: var(--text-rate-level-3);
}
</style>
