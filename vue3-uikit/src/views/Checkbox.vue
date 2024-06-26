<script setup>
  import { ref } from "vue";
  import Checkbox from "@/components/checkbox/Checkbox.vue";
  import CheckboxGroup from "@/components/checkbox/CheckboxGroup.vue";
  
  const checkboxActive = ref(true);
  const checkboxDisabled = ref(true);
  const checkboxDisabledChecked = ref(true)
  
  const listOfHeroes = ref([
    {name: 'Spider Man', id: 'h1'},
    {name: 'Iron Man', id: 'h2'},
    {name: 'Hulk', id: 'h3'},
    {name: 'Thor', id: 'h4'},
    {name: 'Groot', id: 'h5'},
  ])
  const selectedHeroes = ref([])
  const switchTrust = ref(false)
</script>

<template>
    <h1 class="heading-1">Checkbox</h1>
    <h2 class="heading-2">Checkbox Active</h2>
    {{ checkboxActive }}
    <div class="line">
      <Checkbox
        label="Checkbox Active"
        id="checkboxActive"
        name="checkboxActive"
        value="checkboxActive"
        v-model:checked="checkboxActive"
      />
    </div>
  
    <h2 class="heading-2">Checkbox Disabled</h2>
    <div class="line">
      <Checkbox
        label="Checkbox Disabled"
        id="checkboxDisabled"
        name="checkboxDisabled"
        value="checkboxDisabled"
        :disabled="checkboxDisabled"
        v-model:checked="checkboxDisabledChecked"
      />
    </div>
  
    <h2 class="heading-2">Checkbox Group</h2>
    <div class="line--block">
      <p>Selected Heroes: {{ selectedHeroes }}</p>
      <CheckboxGroup v-model:value="selectedHeroes" name="heroes" :options="listOfHeroes"/>
    </div>
  
    <h2 class="heading-2">Switch</h2>
    <div class="line--block">
      <p>Switch: {{ switchTrust }}</p>
      <Checkbox
        label="Trust me?"
        id="switch"
        type="switch"
        name="switch"
        value="Trust me?"
        v-model:checked="switchTrust"
      />
    </div>
  </template>
  <style lang="scss" scoped></style>