<template>
     <div class="searchWrapper">
      <input id="search" name="search" :value="value" @input="handleChange" />
    </div>
</template>

<script>


export default {
    name: 'SearchInput',
    props: {
        value: {
            type: String,
            required: true,
        }
    },
    methods: {
        handleChange(e) {
            this.$emit('input', e.target.value);
        }
    }
}
</script>

<style lang="scss" scoped>

 .searchWrapper {
    display: flex;
    flex-direction: column;
    width: 100%;
    margin-top: 50px;
    justify-content: center;
    align-items: center;
  }

  input {
    height: 30px;
    text-align: center;
    font-size: 18px;
    font-weight: 300;
    background: transparent;
    border: 0;
    color: #ddd;
    border-bottom: 1px solid #ddd;
    transition: box-shadow .5s;

    @media (min-width: 768px) {
        font-size: 24px;
        padding-bottom: 20px;
        width: 400px;
    }

    &::placeholder {
        color: white;
    }

    &:focus {
        outline: none;
        box-shadow: 0 10px 20px -8px rgba(255, 255, 255, .3);
    }
  }
</style>


