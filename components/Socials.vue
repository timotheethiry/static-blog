<template>
    <div class="w-80 h-64 mr-4 p-2 border-2 border-gray-300 shadow-md rounded-lg text-center socials">
        <h2>Find me on </h2>
        <a href="#"><font-awesome-icon :icon="['fab', 'font-awesome']" />Instagram</a>
        <a href="#"><font-awesome-icon :icon="['fab', 'font-awesome']" />Twitter</a>

    </div>
</template>

<style scoped>

@media screen and (max-width: 700px) {

    .socials {
        height: auto;
        width: 50%;
        margin: 0 auto 0;
    }
}

</style>