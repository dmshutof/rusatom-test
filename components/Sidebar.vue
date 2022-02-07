<template>
    <aside class="sidebar">
        <div class="sidebar__header">
            Личный кабинет
        </div>
        <Nav></Nav>
    </aside>
</template>

<script>

import Nav from "./particles/Nav";

export default {
    name: "Sidebar",
    components: {
        Nav
    }
}
</script>

<style lang="scss" scoped>
.sidebar {
    padding: 40px 20px 40px 40px;
    max-width: 264px;
    width: 100%;
    flex-shrink: 1;

    &__header {
        font-weight: 800;
        font-size: 20px;
        line-height: 24px;
        color: #FFFFFF;
        margin-bottom: 32px;
    }
}
</style>
