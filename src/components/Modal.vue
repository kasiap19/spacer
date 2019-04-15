<template v-cloak>
    <transition name="fade">
        <div class="modal-box">
            <div class="modal">
                <div class="modal__pic" style="background-image: url('${this.photo}')" >
                    <img :src="photo" alt="">
                </div>

                <div class="modal__desc">
                    <h2>{{title}}</h2>
                    <p>{{desc}}</p>
                </div>
                <div class="close" @click="$emit('closeModal')"></div>
            </div>
            
        </div>
    </transition>
</template>

<script>
export default {
    name: 'Modal',
    props : {
        item: {
            type: Object,
            required: true,
        }
    },

    data () {
        return {
            photo: null,
            title: null,
            desc: null,
        }
    },

    mounted() {
        this.photo = this.item.links[0].href,
        this.title = this.item.data[0].title,
        this.desc = this.item.data[0].description.substring(0, 200)

        console.log(this.desc)
    }
}
</script>

<style lang="scss" scoped>
[v-cloak] > * { display:none; }
[v-cloak]::before { content: "loading..."; }

    .modal-box {
        background: rgba(30, 61, 74, .6);
        height: 100%;
        position: fixed;
        max-width: 100%;
        top: 0;
        left: 0;

        @media(min-width: 1024px) {
            display: flex;
        }
    }

    .modal {
        background: white;
        display: grid;
        height: 100%;
        padding: 32px;
        justify-content: center;
        align-items: center;
        grid-gap: 20px;

        @media (min-width: 1024px) {
            position: relative;
            grid-template-columns: repeat(2, 1fr);
            height: 80%;
            padding: 50px;
            max-width: 70%;
            bottom: 0;
            left: 0;
            top: 0;
            margin: auto;
            box-shadow: 0 30px 30px -10px rgba(0, 0, 0, .5);
            border: 5px solid #1e3d4a;
        }

        &__pic {
            img {
                width: 100%;
                height: 50%; 
                box-shadow: 0 0 30px rgba(0,0,0, .5);

                @media(min-width: 1024px) {
                    height: 100%;
                }
            }

            margin-top: 50px;

            @media(min-width: 1024px) {
                height: 300px;
                margin-top: 0;
            }
        }

        &__desc {
            color: #333;

            h2 {
                position: relative;

                &::after {
                    content: '';
                    border-bottom: 1px solid #ddd;
                    width: 100%;
                    position: absolute;
                    left: 0;
                    bottom: -5px;
                }
            }
        }
    }

    .close { 
        position: absolute;
        top: 20px;
        right: 20px;
        height: 25px;
        width: 25px;
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;

        &:hover {
          cursor: pointer;

          &::before, &::after {
              background: #ddd;
          }
        }

        &::before,
        &::after {
            content: '';
            position: absolute; 
            width: 20px;
            height: 2px;
            background: #1e3d4a;
            display: block;
        }

        &::before {
            transform: rotate(45deg);
        }

        &:after {
            transform: rotate(-45deg);
        }
    }
    .fade-enter-active, .fade-leave-active {
        transition: opacity .5s;
        }
    .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
        opacity: 0;
    }
</style>
