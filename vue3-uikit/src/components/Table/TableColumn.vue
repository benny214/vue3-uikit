<script setup>
const props = defineProps({
    image: {
        type: Boolean,
        required: false
    },
    srcImage: {
        type: String,
        required: false
    },
    columnTitle: {
        type: String,
        required: false
    }
})
</script>
<template>
    <div class="table__column">
        <span class="table__column-title" v-if="columnTitle">{{ columnTitle }}: </span>
        <slot v-if="!image"></slot>
        <img v-else :src="srcImage" class="table__column-image">
    </div>
</template>

<style lang="scss" scoped>
.table__column {
  padding: 15px 0;
  position: relative;
  &-image {
    max-width: 100%;
    @media screen and (max-width: 767px) {
      max-width: 200px;
    }
  }
  &-title {
    margin-right: 5px;
    display: none;
    font-weight: 600;
    color: #999;
    @media screen and (max-width: 767px) {
      display: inline-block;
    }
  }
}
</style>