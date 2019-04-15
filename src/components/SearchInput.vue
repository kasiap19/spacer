<template>
     <div class="searchWrapper">
      <input id="search" :placeholder="placeholder" name="search" :value="value" @input="handleChange" :class="{dark : dark}" />
    </div>
</template>

<script>


export default {
    name: 'SearchInput',
    data () {
        return {
            placeholder : "e.g. sun",
        }
    },
    props: {
        value: {
            type: String,
            required: true,
        },
        dark: {
            type: Boolean,
            default: false
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
    margin-top: 60px;
    justify-content: center;
    align-items: center;

    @media (min-width: 768px) {
        margin-top: 80px;
    }
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
    transition: box-shadow .3s ease-out;

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
        box-shadow: 0 10px 20px -8px rgba(255, 255, 255, .6);
    }
  }

  .dark {
      color: #1e3d4a;
      border-bottom-color: #1e3d4a;

      &:focus {
        box-shadow: 0 10px 20px -8px (#1e3d4a .2);
      }
  }
</style>


