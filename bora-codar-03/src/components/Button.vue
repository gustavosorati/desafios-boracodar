<template>
  <button :class="[
    variant, 
    disabled ? 'disabled' : '',
    isFocused ? 'focus' : '',
    isLoading ? 'loading' : '',
    isMovable ? 'movable' : ''
  ]">
    <img v-if="isLoading" :class="[isLoading && 'loading']" src="../assets/loading.png" alt="">
    <img v-if="isMovable" src="../assets/movable.png" alt="">
    {{ text }}
  </button>
</template>

<script>
  export default {
    name: "Button",
    props: {
      text: String,
      variant: {
        type: String,
        validator: (value) => {
          return ["primary", "secundary", "tertiary"].includes(value)
        },
        default: "primary"
      },
      disabled: Boolean,
      isFocused: Boolean,
      isLoading: Boolean,
      isMovable: Boolean
    },
  }
</script>

<style>
  button {
    all: unset;
    padding: 12px 24px;
    border-radius: 24px;
    text-transform: uppercase;
    border: 2px solid transparent;
  }

  button.disabled {
    opacity: .6;
  }

  button.focus {
    border-color: #d9cdf7;
  }
  
  button.primary {
    background-color: #8257E5;
  }

  button.primary:hover {
    background-color: #9674E5;
  }

  button.primary:focus {
    background-color: #9674E5;
    border-color: #d9cdf7;
  }

  button.secundary {
    background-color: #3C3748;
  }

  button.secundary:hover {
    background-color: #6A617F;
  }

  button.tertiary {
    background-color: transparent;
  }

  @keyframes rotate {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(360deg);
    }
  }

  button img.loading {
    animation: rotate 2s ease infinite;
  }

  button.loading {
    cursor: wait;
  }

  button.movable {
    cursor: grab;
  }
</style>

