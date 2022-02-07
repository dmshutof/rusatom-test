<template>
    <form @submit.prevent="submit">
        <div class="form__wrapper">
            <div class="input_wrapper">
                <input type="text" class="input" placeholder="Наименование организации"
                       :class="{ 'error': $v.name.$error }"
                       v-model.trim="$v.name.$model">
                <div class="input_description" v-if="$v.name.$error && !$v.name.required">Поле обязательно для заполнения</div>
            </div>
            <div class="input_wrapper">
                <input type="email" class="input" placeholder="Имейл" v-model.trim="$v.email.$model"
                       :class="{ 'error': $v.email.$error }">
                <div class="input_description" v-if="$v.email.$error && !$v.email.required">Поле обязательно для заполнения</div>
                <div class="input_description" v-if="$v.email.$error && !$v.email.email">Некорректный Имейл</div>
            </div>
            <div class="input_wrapper">
                <multiselect class="input" v-model.trim="$v.status.$model" :options="options" placeholder="Статус"
                             :class="{ 'error': $v.status.$error }"
                             :searchable="false">
                    <template slot="caret">
                        <svg class="caret" width="16" height="6" viewBox="0 0 16 6" fill="none"
                             xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M13.9587 0.162237C14.423 -0.136817 15.0418 -0.00284818 15.3409 0.461463C15.449 0.629235 15.5005 0.817181 15.5003 1.00292C15.5 1.33124 15.3382 1.65268 15.0417 1.84368L9.62463 5.33268C9.622 5.33437 9.61938 5.33605 9.61676 5.33773L9.08314 5.68142C8.42364 6.10619 7.5767 6.10619 6.9172 5.68142L6.38355 5.33771C6.38094 5.33603 6.37832 5.33436 6.37571 5.33268L0.958696 1.84367C0.784575 1.73153 0.656917 1.5744 0.581124 1.39733C0.474246 1.14763 0.47051 0.858256 0.585097 0.599328C0.605942 0.552224 0.630704 0.506128 0.659473 0.461462C0.958527 -0.00284932 1.57736 -0.136817 2.04167 0.162238L7.45869 3.65126L7.46324 3.65417C7.79081 3.86267 8.20954 3.86267 8.53711 3.65417L13.9587 0.162237Z"
                                fill="#3D75E4"/>
                        </svg>
                    </template>
                </multiselect>
                <div class="input_description" v-if="$v.status.$error && !$v.status.required">Поле обязательно для заполнения</div>
            </div>
            <div class="map">
                <yandex-map
                    :coords="[56.326797, 44.006516]"
                    style="width: 500px; height: 480px;"
                    map-type="hybrid"
                    zoom="9"
                >
                    <ymap-marker
                        :coords="[56.326797, 44.006516]"
                        marker-id="123"
                    />
                </yandex-map>
            </div>
        </div>
        <button type="submit" :disabled="$v.$invalid">
            Сохранить
        </button>
    </form>
</template>

<script>
import Multiselect from 'vue-multiselect'
import {required,email} from 'vuelidate/lib/validators'

export default {
    name: "Form",
    components: {
        Multiselect
    },
    data() {
        return {
            name: '',
            email: '',
            status: '',
            options: ['Статус 1', 'Статус 2'],
            submitStatus: ''
        }
    },
    validations: {
        name: {
            required
        },
        email: {
            required,
            email
        },
        status: {
            required
        }
    },
    methods: {
        submit() {
            this.$v.$touch()
            if (this.$v.$invalid) {
                this.submitStatus = 'ERROR'
                console.log('ERROR')
            } else {
                this.submitStatus = 'PENDING'
                setTimeout(() => {
                    console.log({
                        organization_name: this.name,
                        email: this.email,
                        status: this.status,
                    })
                    this.submitStatus = 'OK'
                    this.name = ''
                    this.email = ''
                    this.status = ''
                    this.$v.$reset()
                }, 500)

            }
        }
    }
}
</script>

<style lang="scss">

$titanic: #04153E;
$titanic-light: rgba($titanic, .7);
form {
    margin-top: 36px;

    .form__wrapper {
        display: grid;
        grid-row-gap: 24px;
        grid-column-gap: 16px;
        grid-template-columns: auto 500px;
        grid-template-rows: 40px 40px 40px auto;
        align-items: start;
    }
}

.input {
    font-size: 16px;
    line-height: 20px;
    color: $titanic;
    padding: 10px 16px;
    height: 40px;
    width: 100%;
    border: none;
    border-radius: 8px;
    background: rgba(#3D75E4, .08);

    &::-webkit-input-placeholder {
        color: rgba($titanic, .5);
    }

    &:-ms-input-placeholder {
        color: rgba($titanic, .5);
    }

    &::-moz-placeholder {
        color: rgba($titanic, .5);
        opacity: 1;
    }

    &:-moz-placeholder {
        color: rgba($titanic, .5);
        opacity: 1;
    }

    * {
        font-size: 16px;
        line-height: 20px;
        color: $titanic;
    }

    &.error {
        border-color: #ff604f !important;
        animation-name: shakeError;
        animation-fill-mode: forwards;
        animation-duration: .6s;
        animation-timing-function: ease-in-out;

    }

    &_wrapper {
        position: relative;
    }

    @keyframes shakeError {
        0% {
            transform: translateX(0);
        }
        15% {
            transform: translateX(0.375rem);
        }
        30% {
            transform: translateX(-0.375rem);
        }
        45% {
            transform: translateX(0.375rem);
        }
        60% {
            transform: translateX(-0.375rem);
        }
        75% {
            transform: translateX(0.375rem);
        }
        90% {
            transform: translateX(-0.375rem);
        }
        100% {
            transform: translateX(0);
        }
    }

    &_description {
        position: absolute;
        left: 0;
        top: calc(100% + 2px);
        font-size: 10px;
        line-height: 13px;
        letter-spacing: -.02em;
        color: #ff604f;
    }
}

.map {
    grid-column: 2/3;
    grid-row: 1/5;
}

.multiselect {
    cursor: pointer;
    position: relative;

    .caret {
        position: absolute;
        top: 50%;
        right: 16px;
        margin-top: -3px;
        transition: .2s ease-in-out;
    }

    &.multiselect--active {
        .caret {
            transform: rotate(180deg);
        }
    }
}

.multiselect__input {
    color: $titanic;
}

.multiselect__placeholder {
    color: rgba($titanic, .5);
}

.multiselect__content-wrapper {
    color: $titanic;
    width: 100%;
    position: absolute;
    left: 0;
    top: calc(100% + 8px);
    border-radius: 8px;
    overflow: hidden;
    background: rgba(#3D75E4, .1);

    li .multiselect__option {
        display: block;
        padding: 10px 16px;
        width: 100%;

        &:hover {
            background: rgba(#3D75E4, .15);
        }

        &.multiselect__option--selected {
            background: rgba(#3D75E4, .15);
        }
    }
}

.multiselect__content {
    width: 100%;
}

button {
    width: 100%;
    background: #3D75E4;
    border-radius: 8px;
    border: none;
    font-size: 16px;
    line-height: 20px;
    color: #FFFFFF;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px 16px;
    margin-top: 30px;
    cursor: pointer;
    transition: .2s ease-in-out;

    &:disabled {
        opacity: .4;
        pointer-events: none;
    }

    &:hover {
        opacity: .9;
    }

    &:active {
        transform: scale(1.01);
    }
}
</style>
