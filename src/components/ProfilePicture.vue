<script setup>
// Profile picture is a map with possible sources for it, eg. webp, png
defineProps({
    picture: {
        type: Object,
        required: true
    },
    name: {
        type: String,
        required: true
    }
})
</script>

<template>
    <div class="profile-picture">
        <picture>
            <source :srcset="picture.webp" type="image/webp">
            <source :srcset="picture.png" type="image/png">
            <img :src="picture.png" :alt="name">
        </picture>
    </div>
</template>

<style scoped>
.profile-picture {
    height: 2rem;
    width: 2rem;
    border-radius: 2rem;
}
picture {
    display: block;
    width: 100%;
}
</style>