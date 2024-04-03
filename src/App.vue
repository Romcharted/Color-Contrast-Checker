<template>
    <div class="app-container">
        <h1>Color Contrast Checker</h1>
        <p class="app-desc">
            Calculate the contrast ratio of text and background colors.
        </p>

        <div class="explain-container">
            <h3>How does it work?</h3>
            <p>
                This tool follows the Web Content Accessibility Guidelines
                (WCAG), which are a series of recommendations for making the web
                more accessible.<br />

                Regarding colors, the standard defines two levels of contrast
                ratio: AA (minimum contrast) and AAA (enhanced contrast).<br />

                The level AA requires a contrast ratio of at least 4.5:1 for
                normal text and 3:1 for large text (at least 18pt) or bold
                text.<br />

                The level AAA requires a contrast ratio of at least 7:1 for
                normal text and 4.5:1 for large text or bold text.<br />
            </p>

            <a
                href="https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines"
                target="_blank"
                >Learn more</a
            >
        </div>
    </div>
</template>

<script setup lang="ts"></script>

<style>
.app-container {
    display: flex;
    flex-direction: column;
    padding: 20px;
    width: 100%;
    height: 100vh;
    align-items: center;
    justify-content: center;

    font-family: "Inter", sans-serif;
}

h1 {
    font-size: 50px;
    margin-bottom: 30px;
    font-weight: 900;
    color: var(--main-color);
}

.app-desc {
    font-size: 20px;
    color: var(--text-color-light);
}

.explain-container {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    gap: 20px;
}

.explain-container h3 {
    font-size: 24px;
    font-weight: 900;
}

.explain-container a {
    color: #0066ff;
}
</style>
