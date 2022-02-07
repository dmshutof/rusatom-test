<template>
    <nav>
        <ul>
            <NavItem v-for="(link,index) of links" :key="index" :link="link"></NavItem>
        </ul>
    </nav>
</template>

<script>
import NavItem from "./NavItem";

export default {
    name: "Nav",
    components: {
        NavItem
    },
    data() {
        return {
            links: [
                {
                    title: "Дашборд",
                    url: "#",
                    active: false,
                    icon: "statistics_16.svg",
                    submenu: [],
                },
                {
                    title: "Ситуационный центр",
                    url: "#",
                    active: false,
                    icon: "new_16.svg",
                    submenu: [],
                },
                {
                    title: "Активный гражданин",
                    url: "#",
                    active: false,
                    icon: "active-citizen_16.svg",
                    submenu: [],
                },
                {
                    title: "Службы города",
                    active: false,
                    icon: "mncpl-control_16.svg",
                    submenu: [
                        {
                            title: "Семинары и курсы",
                            url: "#",
                            active: true,
                            submenu: []
                        },
                        {
                            title: "Вебинары",
                            url: "#",
                            active: false,
                            submenu: []
                        },
                        {
                            title: "Самообучение",
                            url: "#",
                            active: false,
                            submenu: []
                        },
                        {
                            title: "Тьютор",
                            url: "#",
                            active: false,
                            submenu: []
                        }
                    ],
                },
                {
                    title: "Бизнес",
                    active: false,
                    icon: "business-case_16.svg",
                    submenu: [
                        {
                            title: "Семинары и курсы",
                            url: "#",
                            active: true,
                            submenu: []
                        },
                        {
                            title: "Вебинары",
                            url: "#",
                            active: false,
                            submenu: []
                        },
                        {
                            title: "Самообучение",
                            url: "#",
                            active: false,
                            submenu: []
                        },
                        {
                            title: "Тьютор",
                            url: "#",
                            active: false,
                            submenu: []
                        }
                    ],
                },
                {
                    title: "Платные услуги",
                    active: false,
                    icon: "payment-wallet_16.svg",
                    submenu: [
                        {
                            title: "Семинары и курсы",
                            url: "#",
                            active: true,
                            submenu: []
                        },
                        {
                            title: "Вебинары",
                            url: "#",
                            active: false,
                            submenu: []
                        },
                        {
                            title: "Самообучение",
                            url: "#",
                            active: false,
                            submenu: []
                        },
                        {
                            title: "Тьютор",
                            url: "#",
                            active: false,
                            submenu: []
                        }
                    ],
                },
                {
                    title: "Безопасность",
                    active: false,
                    icon: "security_16.svg",
                    submenu: [
                        {
                            title: "Семинары и курсы",
                            url: "#",
                            active: true,
                            submenu: []
                        },
                        {
                            title: "Вебинары",
                            url: "#",
                            active: false,
                            submenu: []
                        },
                        {
                            title: "Самообучение",
                            url: "#",
                            active: false,
                            submenu: []
                        },
                        {
                            title: "Тьютор",
                            url: "#",
                            active: false,
                            submenu: []
                        }
                    ],
                },
                {
                    title: "Инфраструктура",
                    active: false,
                    icon: "avatar_16.svg",
                    submenu: [
                        {
                            title: "ГИС ЖКХ",
                            url: "#",
                            active: true,
                            icon: "cold-water_16.svg",
                            submenu: []
                        },
                        {
                            title: "АСУДД",
                            url: "#",
                            active: true,
                            icon: "canalization_16.svg",
                            submenu: []
                        },
                        {
                            title: "Электропитание",
                            url: "#",
                            active: false,
                            icon: "electric-power_16.svg",
                            submenu: []
                        },
                        {
                            title: "БС сотовой связи",
                            url: "#",
                            active: false,
                            icon: "telephone_16.svg",
                            submenu: []
                        },
                        {
                            title: "Мусор",
                            url: "#",
                            active: false,
                            icon: "tko_16.svg",
                            submenu: []
                        },
                        {
                            title: "Счетчики",
                            url: "#",
                            active: false,
                            icon: "dash_16.svg",
                            submenu: []
                        },
                        {
                            title: "Диспетчер лифтов",
                            url: "#",
                            active: false,
                            icon: "monitoring_16.svg",
                            submenu: []
                        },
                        {
                            title: "Инженерные сети",
                            url: "#",
                            active: false,
                            icon: "energy-supply_16.svg",
                            submenu: []
                        },
                        {
                            title: "Дворы",
                            url: "#",
                            active: false,
                            icon: "child-playground_16.svg",
                            submenu: []
                        },
                        {
                            title: "ИСОГД",
                            url: "#",
                            active: false,
                            icon: "heat_16.svg",
                            submenu: []
                        },
                        {
                            title: "Контроль",
                            url: "#",
                            active: false,
                            icon: "monitoring_16.svg",
                            submenu: []
                        },
                    ],
                },

            ]
        }
    }
}
</script>

<style lang="scss">
nav {


    ul {
        li {
            svg {
                margin-left: 12px;

                &.rotate {
                    transform: rotate(180deg);
                }
            }

            a {
                position: relative;
                font-weight: 500;
                font-size: 16px;
                line-height: 125%;
                height: 44px;
                z-index: 1;
                display: flex;
                align-items: center;
                cursor: pointer;
                user-select: none;
                color: rgba(255, 255, 255, .7);

                img {
                    flex-shrink: 1;
                    width: 16px;
                    height: 16px;
                    margin-right: 12px;
                }

                &:after {
                    content: '';
                    background-color: #04153E;
                    background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg width='4' height='32' viewBox='0 0 4 32' fill='none' xmlns='http://www.w3.org/2000/svg'%3e%3cpath d='M0 0C2.20914 0 4 1.79086 4 4V28C4 30.2091 2.20914 32 0 32V0Z' fill='%233D75E4'/%3e%3c/svg%3e ");
                    background-repeat: no-repeat;
                    background-position: left center;
                    position: absolute;
                    width: calc(100% + 60px);
                    height: 100%;
                    left: -40px;
                    top: 0;
                    z-index: -1;
                    opacity: 0;
                    transition: .2s ease-in-out;
                }

                &:hover {
                    &:after {
                        opacity: 1;
                    }

                }
            }

            ul {
                li {
                    padding-left: 28px;
                    position: relative;
                    z-index: 1;
                    a{
                        &:after {
                            width: calc(100% + 88px);
                            height: 100%;
                            left: -68px;
                        }
                    }
                    &.active {
                        &:after {
                            opacity: 1;
                        }
                    }
                }
            }
        }
    }
}
</style>
