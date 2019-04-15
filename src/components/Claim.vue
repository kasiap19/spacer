<template>
    <div class="claim">
        <h1 class="claim__title">
            SPACER     
            <font-awesome-icon icon="space-shuttle" />
        </h1>
        <p class="claim__desc">
            Begin your journey through our amazing galaxy 
            and discover places you never even heard of.
        </p>
        <p class="claim__desc">
            Type anything space-related to start.
        </p>
    </div>
</template>

<script>
export default {
    name: 'Claim'
}
</script>

<style lang="scss">
    .claim {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        padding-top: 50px;

        &__title {
            position: relative;
            font-size: 50px;
            margin: 0;
            color: #fff;
            font-weight: 800;
            display: flex;
            align-items: center;

            @media (min-width: 768px) {
                font-size: 80px;
                line-height: 1;
                letter-spacing: 1px;
            }

            svg {
                position: absolute;
                margin-left: 0px;
                margin-top: -5px;
                opacity: .5;
                left: -40px;
                color: orange;
                font-size: 80px;
                transform: rotate(-45deg);
                z-index: -1;
            }   

            &--dark {
                position: relative;
                font-size: 50px;
                margin: 0;
                color: #1e3d4a;
                font-weight: 800;
                display: flex;
                align-items: center;
                padding-top: 32px;

            @media (min-width: 768px) {
                font-size: 50px;
                line-height: 1;
                letter-spacing: 1px;
            }

                svg {
                    position: absolute;
                    margin-left: 0px;
                    margin-top: -5px;
                    opacity: .5;
                    left: -40px;
                    color: orange;
                    font-size: 50px;
                    transform: rotate(-45deg);
                    z-index: -1;

                    @media(min-width: 1024px) {
                        font-size: 70px;
                    }

                }
            }

        }

        &__desc {
            color: #bbbbbb;
            font-size: 15px;
            margin-top: 13px;

            @media (min-width: 768px) {
                font-size: 18px;
                max-width: 500px;
                line-height: 1.5;
                letter-spacing: 1px;
            }
        }
    }
</style>


