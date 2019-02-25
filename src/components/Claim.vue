<template>
    <div class="claim">
        <h1 class="claim__title">SPACER</h1>
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

<style lang="scss" scoped>
    .claim {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        
        padding-top: 50px;

        &__title {
            &::first-letter {
                color: orange;
            }

            &::after {
                content: '.';
                color: orange;
                padding-left: 10px;
            }

            position: relative;
            font-size: 50px;
            margin: 0;
            color: #fff;
            font-weight: 800;

            @media (min-width: 768px) {
                font-size: 80px;
                line-height: 1;
                letter-spacing: 1px;
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


