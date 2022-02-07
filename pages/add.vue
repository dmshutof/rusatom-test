<template>
    <div class="container">
        <scroll-bar>
            <Sidebar></Sidebar>
        </scroll-bar>
        <Main></Main>
    </div>
</template>

<script>
import ScrollBar from 'vue-smooth-scrollbar'

export default {
    name: "add",
    components: {
        ScrollBar
    },
}
</script>

<style lang="scss">

body {
    background: #091F52;
}

a {
    text-decoration: none;
}

.fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
}

.fade-enter, .fade-leave-to {
    opacity: 0;
}

.container {
    display: flex;
    max-height: 768px;
}

.vue-smooth-scrollbar {
    width: 100%;
    max-width: 264px;
    position: relative;
    max-height: 768px;
}

.scrollbar-track {
    background: transparent !important;
}

.scrollbar-track-y {
    width: 6px !important;
}

.scrollbar-thumb {
    width: 4px !important;
    background: rgba(#E4EDFB, .5) !important;
    border-radius: 2px !important;
}
</style>
