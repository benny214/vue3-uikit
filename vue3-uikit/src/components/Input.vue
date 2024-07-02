<script setup>
const emit = defineEmits(["update:value"]);
const props = defineProps({
  value: {
    type: String,
    default: "",
  },
  name: {
    type: String,
    required: true,
  },
  type: {
    type: String,
    default: "text",
  },
  placeholder: {
    type: String,
    default: "",
  },
  label: {
    type: String,
    required: true,
  },
  width: {
    type: String,
    default: "300px",
  },
  error: {
    type: Array,
    required: false,
  },
});

const updateValue = (e) => {
  emit("update:value", e.target.value);
};
</script>
<template>
    <div class="form__input">
        <input
          class="input__text"
          :type="type"
          :name="name"
          :id="name"
          :placeholder="placeholder"
          :value="value"
          @input="updateValue"
        />
        <label :for="name" class="input__label">{{ label }}</label>
        <TransitionGroup>
          <div v-for="element of error" :key="element.$uid" class="form__error">
            <div class="form-error__message">{{ element.$message }}</div>
          </div>
        </TransitionGroup>
    </div>
</template>
<style lang="scss" scoped>
    .form {
      &__input {
        margin-bottom: 30px;
        position: relative;
      }
      &__error {
        background: var(--danger);
        margin-top: 4px;
        border-radius: 7px;
        font-size: 13px;
        color: #fff;
        padding: 5px;
      }
    }
    .input {
      &__text {
        border: 1px solid var(--primary);
        padding: 0 10px;
        height: 40px;
        border-radius: 7px;
        font-size: 15px;
        width: 100%;
        position: relative;
        z-index: 1;
        &:focus {
          & + .input__label {
            z-index: 1;
            opacity: 1;
            top: -20px;
          }
        }
        &:not(:placeholder-shown) {
          & + .input__label {
            z-index: 1;
            opacity: 1;
            top: -20px;
          }
        }
      }
      &__label {
        font-weight: bold;
        display: block;
        position: absolute;
        top: 20px;
        opacity: 0;
        z-index: -1;
        transition: 0.3s;
        font-size: 13px;
        color: var(--primary);
      }
    }
    
    .v-enter-active,
    .v-leave-active {
      transition: opacity 0.5s ease;
    }
    
    .v-enter-from,
    .v-leave-to {
      opacity: 0;
    }
    
    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }
    
    input[type="number"] {
      -moz-appearance: textfield;
    }
</style>