<script setup>
// Profile picture is a map with possible sources for it, eg. webp, png
const props = defineProps({
    picture: {
        type: Object,
        required: true
    },
    name: {
        type: String,
        required: true
    }
})

const images = [];
for (const [key, value] of Object.entries(props.picture)) {
    images.push({
        src: `/${value}`,
        type: `image/${key}`,
    });
}

// Get the first png
const defaultImage = images.find(image => image.type === 'image/png');
</script>

<template>
    <div class="profile-picture">
        <picture>
            <source v-for="picture of images" 
                :key="picture.type" 
                :srcset="picture.src" 
                :type="picture.type"
            >
            <img :src="defaultImage.src" :alt="name">
        </picture>
    </div>
</template>

<style scoped>
.profile-picture {
    height: 2rem;
    width: 2rem;
    border-radius: 2rem;
}
picture, img {
    display: block;
    width: 100%;
    height: auto;
}
</style>