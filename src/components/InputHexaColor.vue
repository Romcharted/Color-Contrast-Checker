<template>
    <div class="input-hexa-color">
        <label>{{ title }}</label>
        <input
            type="text"
            v-model="color"
            @keyup.enter="verificationEntry"
            @blur="verificationEntry"
        />
    </div>
</template>

<script setup lang="ts">
import { ref, defineEmits } from "vue";

const props = defineProps({
    defaultValue: String,
    title: String,
});

const emit = defineEmits(["colorChanged"]);

let color = ref(props.defaultValue || "");

const verificationEntry = () => {
    // Supprimer les caractères non hexadécimaux
    color.value = color.value.replace(/[^a-fA-F0-9]/g, "");

    // Ajouter '#' au début de la nouvelle valeur si il y en a pas
    if (!color.value.startsWith("#")) {
        color.value = "#" + color.value;
    }

    // Taille de 7 max (en comptant le #)
    color.value = color.value.substring(0, 7);

    // On met en majuscule
    color.value = color.value.toUpperCase();

    // On converti si c'est un hex court
    color.value = expandShortHex(color.value);

    // Si c'est tout bon, on donne la valeur au parent
    if (color.value.length == 7) {
        emit("colorChanged", color.value);
    }
};

// Permet de convertir un short hex -> hex
const expandShortHex = (hex: string): string => {
    // Vérifier si la couleur est une abréviation hexadécimale de trois caractères
    if (hex.length === 4 && hex[0] === "#") {
        return "#" + hex[1] + hex[1] + hex[2] + hex[2] + hex[3] + hex[3];
    }
    return hex;
};
</script>

<style>
.input-hexa-color {
    display: flex;
    flex-direction: column;
    gap: 14px;
    width: 100%;
}

.input-hexa-color label {
    color: black;
    font-size: 13px;
    font-weight: 500;
}

.input-hexa-color input {
    border-radius: 10px;
    height: 46px;
    padding: 0 50px 0 14px;
    font-size: 15px;
    transition: border 0.1s;
    border: 1px solid #d8d8da !important;
    width: 100%;
    color: black !important;
    font-family: "Inter", sans-serif;
}

.input-hexa-color input:focus,
.input-hexa-color input:focus-visible {
    outline: none;
    border: 1px solid #0066ff !important;
}
</style>
