
<script setup>
const props = defineProps({
  label: {
    type: String,
    default: 'Кнопка'
  },
  color: {
    type: String,
    default: 'primary'
  },
  rounded: {
    type: Boolean,
    required: false
  },
  disabled: {
    type: Boolean,
    required: false
  },
  outlined: {
    type: Boolean,
    required: false
  },
  icon: {
    type: String,
    required: false
  },
  size: {
    type: String,
    default: 'normal'
  },
})

</script>
<template>
    <button 
    :class="[
      'btn', 
      `btn--${color}`, 
      {'btn--rounded': rounded},
      {'btn--outlined': outlined},
      {'btn--icon': icon},
      {'btn--large': size === 'large'} ]" 
      :disabled="disabled">
      <span v-if="icon">
        <font-awesome-icon :icon="`fa-regular fa-${icon}`" />
      </span>
      <span v-else> {{ label }}</span>
        
      </button>
</template>
<style lang="scss" scoped>
.btn {
  margin-right: 10px;
  margin-bottom: 10px;
  padding: 0 20px;
  height: 40px;
  color: #fff;
  border-radius: 7px;
  border: none;
  cursor: pointer;
  font-size: 15px;
  line-height: 6px;
  transition: .2s;
  &--primary {
    background-color: var(--primary);
    border: 1px solid var(--primary);
    &:enabled:hover {
      background-color: var(--primary-h);
      border-color: var(--primary-h);
    }
  }
  &--secondary {
    background-color: var(--secondary);
    border: 1px solid var(--secondary);
    &:enabled:hover {
      background-color: var(--secondary-h);
      border-color: var(--secondary-h);
    }
  }
  &--success {
    background-color: var(--success);
    border: 1px solid var(--success);
    &:enabled:hover {
      background-color: var(--success-h);
      border-color: var(--success-h);
    }
  }
  &--info {
    background-color: var(--info);
    border: 1px solid var(--info);
    &:enabled:hover {
      background-color: var(--info-h);
      border-color: var(--info-h);
    }
  }
  &--warning {
    background-color: var(--warning);
    border: 1px solid var(--warning);
    &:enabled:hover {
      background-color: var(--warning-h);
      border-color: var(--warning-h);
    }
  }
  &--danger {
    background-color: var(--danger);
    border: 1px solid var(--danger);
    &:enabled:hover {
      background-color: var(--danger-h);
      border-color: var(--danger-h);
    }
  }

  &--rounded {
    border-radius: 15px;
  }

  &:disabled {
    opacity: .6;
    cursor: default;
    &:enabled:hover {
      opacity: .6;
    }
  }

  &--outlined {
    background-color: transparent;
    color: #000;
    &:hover {
      color: #fff;
    }
  }

  &--icon {
    padding: 0;
    width: 40px;
    height: 40px;
    border-radius: 50%;
  }

  &--large {
    height: 48px;
    padding: 0 30px;
  }
}
</style>