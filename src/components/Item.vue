<template>
   <div :style="styles" class="item">
       <div class="item__desc">
           <h3>{{title}}</h3>
       </div>
   </div>

</template>

<script>
export default {
    name: 'Item',
    props: {
    item: {
            type: Object,
            required: true,
        },
    },
   
    data() {
        return {
            photo: this.item.links[0].href,
            title: this.item.data[0].title,
        }
    },

    computed: {
        styles() {
            return `background-image: url("${this.photo}")`;
        }
    }
}
</script>


<style lang="scss" scoped>
    .item {
        &:hover {
            .item__desc {
                opacity: 1;
            }

            cursor: pointer;
        }
        height: 200px;
        width: 300px;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: 50%;

        @media(min-width: 1024px) {
            height: 300px;
        }

        &__desc {
            background: rgba(30, 61, 74, .6);
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 30px;
            box-shadow: 0 30px 30px -10px rgba(0, 0, 0, .3);
            transition: .3s;

            @media(min-width: 1024px) {
                opacity: 0;
            }

            h3 {
                color: #ddd;
                font-weight: 400;
                letter-spacing: 1px;
                text-align: center;
                line-height: 24px;
                border-bottom: 1px solid  #ddd;
                padding: 10px;
            }
        }
    }
</style>
