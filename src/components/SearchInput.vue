<template>
    <div class="search">
      <input 
        placeholder="Enter the name..."
        :class="{ ifDarkClass: dark }"
        :value="value"
        @input="handleChange"
      />
    </div>
</template>

<script>
    export default {
        name: 'searchInput',
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
            },
        },
    };
</script>

<style lang="scss" scoped>
  .search {
    display: flex;
    flex-direction: column;
    width: 300px;
    margin-bottom: 40px;

    input {
      height: 30px;
      border: none;
      border-bottom: 1px solid #00081c;
      background: none;
      color: #00081c;
      transition: box-shadow 0.7s;
      text-align: center;
      font-size: 20px;
      
      &::placeholder {
          color: #00081c;
          font-size: 20px;
          opacity: 0.95;
      }

      @media (min-width: 768px) {
          font-size: 28px;
      }
    }
    input:focus {
        outline: none;
        box-shadow: 0 15px 25px -10px #6b7077;

        @media (min-width: 768px) {
            box-shadow: 0 15px 25px -10px #6b7077;
        }
    }
    .ifDarkClass {
        color: #546e99;
        border-bottom-color: #546e99;
    }
    .ifDarkClass:focus {
        box-shadow: 0 15px 25px -10px #546e99;
    }
  }
</style>