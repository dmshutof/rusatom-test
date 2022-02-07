<template>
    <main class="main">
        <div class="main__header">
            <NuxtLink to="/" class="backlink">
                <svg width="5" height="12" viewBox="0 0 5 12" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                        d="M4.84186 1.53714C5.13851 1.07129 5.00135 0.453158 4.5355 0.156507C4.06965 -0.140144 3.45152 -0.00298109 3.15487 0.462869L0.312938 4.92573C-0.104404 5.58111 -0.104404 6.41889 0.312938 7.07427L3.15487 11.5371C3.45152 12.003 4.06965 12.1402 4.5355 11.8435C5.00135 11.5468 5.13851 10.9287 4.84186 10.4629L2.34198 6.53714C2.34189 6.537 2.34207 6.53728 2.34198 6.53714C2.13358 6.20951 2.1334 5.79042 2.34198 5.46287L4.84186 1.53714Z"
                        fill="#3D75E4"/>
                </svg>
                Назад
            </NuxtLink>
            <div class="user">
                <div class="user__image">
                    <img src="~/assets/images/Avatar.jpg" alt="">
                </div>
                <div class="user__name">
                    Александра
                </div>
                <div class="user__position">
                    Должность
                </div>
            </div>
        </div>
        <h1>Добавление организации</h1>
        <p>Поставщик</p>
        <added-form></added-form>
    </main>
</template>

<script>
import AddedForm from './particles/AddedForm'

export default {
    name: "Main",
    components: {
        AddedForm
    }
}
</script>

<style scoped lang="scss">

$titanic: #04153E;
$titanic-light: rgba($titanic, .7);


.main {
    background: #FFFFFF;
    border-radius: 48px 0px 0px 0px;
    padding: 32px 40px 40px 32px;
    width: 100%;
    min-height: 100vh;

    &__header {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 12px;

        .backlink {
            svg {
                margin-right: 8px;
            }

            display: flex;
            align-items: center;
            font-weight: 500;
            font-size: 16px;
            line-height: 124%;
            color: #3D75E4;
        }

        .user {
            display: grid;
            grid-template-columns: 40px auto;
            grid-column-gap: 8px;
            align-items: center;

            &__image {
                grid-row: 1/3;
                width: 40px;
                height: 40px;
                border-radius: 50%;
                overflow: hidden;

                img {
                    width: 100%;
                    height: 100%;
                    object-fit: cover;
                    object-position: center center;
                }
            }

            &__name {
                font-weight: 800;
                font-size: 13px;
                color: $titanic;
                line-height: 124%;
            }

            &__position {
                font-size: 10px;
                line-height: 120%;
                color: $titanic-light;
            }
        }
    }
}

h1 {
    font-weight: 800;
    font-size: 28px;
    line-height: 114%;
    color: $titanic;
    margin-bottom: 8px;
}

p {
    font-size: 16px;
    line-height: 125%;
    color: rgba($titanic, .5);
}


</style>
