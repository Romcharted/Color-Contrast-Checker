<template>
    <div class="input-hexa-color">
        <input
            v-model="color"
            @keyup.enter="verificationEntry"
            @blur="verificationEntry"
        />
        {{ color }}
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

let color = ref("");

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
    } else {
        // mettre un message en rouge pour dire que la couleur n'est pas valide
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
