<template>
    <transition name="fade">
    <div class="wrapperOut">
        <div class="modalowyWrapper">
            <div class="photo">
                <img :src="photo" />
            </div>
            <div class="descriptionAll">
                <h2 class="title">
                    {{title}}
                </h2>
                <p class="descriptionOfItem">
                    {{describe}}
                </p>
            </div>
        </div>
        <div class="close" @click="$emit('closeModal')">

        </div>
    </div>
    </transition>
</template>

<script>
    export default {
        name: 'Modal',
        props: {
            item: {
                type: Object,
                required: true,
            },
        },
        data() {
            return {
                title: this.item.data[0].title,
                describe: this.item.data[0].description.substring(0, 300),
                photo: this.item.links[0].href,
            };
        },

        };
</script>

<style lang="scss" scoped>
    .close {
        position: absolute;
        right: 25px;
        top: 20px;
        cursor: pointer;
        padding-right: 20px;
        padding-bottom: 10px;
        padding-top: 10px;

        &::before,
        &::after {
            position: absolute;
            content: '';
            width: 20px;
            height: 2px;
            background: black;
            display: block;
        } 

        &::before {
            transform: rotate(45deg);
        }
        &::after {
            transform: rotate(-45deg);
        }
    }

    .wrapperOut {
        z-index: 100;
        width: 70%;
        height: 90%;
        position: fixed;
        background-color: lightgray;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        border: 1px solid darkslategrey;

        @media (min-width: 1024px) {
            height: 70%;
            
        }
    }

    .modalowyWrapper {
        display: flex;
        height: auto;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        padding: 20px; 
        align-content: center;

        .photo {
            max-width: 75%;
            max-height: 350px;
            background: block;
            margin-bottom: 20px;
            margin-top: 35px;

            img {
                width: 90%;
                max-height: 360px;
            }
          
        }
        .descriptionAll {
            .title {
                font-size: 18px;
            }
            .descriptionOfItem {
                font-size: 14px;
            }
        }

        @media (min-width: 1024px) {
            flex-direction: inherit; 

            .photo {
                max-width: 60%;
                margin-bottom: 10px;
                padding-bottom: 0;
                margin-left: 15px;

                img {
                    width: 100%;
                    max-height: 350px;
                }
            }
            .descriptionAll {
                margin-left: 15px;
                max-width: 50%;

                .title {
                    font-size: 20px;
                }
                .descriptionOfItem {
                    font-size: 16px;
                }
            }
        }
    }
    .fade-enter-active, .fade-leave-active {
        transition: opacity 0.01s ease-in-out;
    }
    .fade-enter, .fade-leave-to {
        opacity: 0;
    }
</style>
