<script setup>
import Button from '@/components/Button.vue'

const eventForBtn = () => {
  alert('Clicked!')
}
</script>

<template>
  <h1 class="heading-1">Кнопки</h1>
  <br>
  <h2 class="heading-2">Событие на клик</h2>
  <div class="line">
    <Button label="Нажми меня!" color="danger" @click="eventForBtn"/>
  </div>

  <h2 class="heading-2">Цвета</h2>
  <div class="line">
    <Button label=".primary" color="primary"/>
    <Button label=".secondary" color="secondary"/>
    <Button label=".success" color="success"/>
    <Button label=".info" color="info"/>
    <Button label=".warning" color="warning"/>
    <Button label=".danger" color="danger"/>
  </div>

  <h2 class="heading-2">Скругленные кнопки</h2>
  <div class="line">
    <Button label=".primary" color="primary" rounded/>
    <Button label=".secondary" color="secondary" rounded/>
    <Button label=".success" color="success" rounded/>
    <Button label=".info" color="info" rounded/>
    <Button label=".warning" color="warning" rounded/>
    <Button label=".danger" color="danger" rounded/>
  </div>

  <h2 class="heading-2">Задизейбленные кнопки</h2>
  <div class="line">
    <Button label=".primary" color="primary"/>
    <Button label=".secondary" color="secondary" disabled/>
    <Button label=".success" color="success"/>
    <Button label=".info" color="info" disabled/>
    <Button label=".warning" color="warning"/>
    <Button label=".danger" color="danger" disabled/>
  </div>

  <h2 class="heading-2">Outlined кнопки</h2>
  <div class="line">
    <Button label=".primary" color="primary" outlined/>
    <Button label=".secondary" color="secondary" outlined/>
    <Button label=".success" color="success" outlined/>
    <Button label=".info" color="info" outlined/>
    <Button label=".warning" color="warning" outlined/>
    <Button label=".danger" color="danger" outlined/>
  </div>

  <h2 class="heading-2">Кнопки с иконками</h2>
  <div class="line">
    <Button icon="heart" color="primary"/>
    <Button icon="hand" color="secondary"/>
    <Button icon="address-book" color="success"/>
    <Button icon="credit-card" color="info"/>
    <Button icon="lemon" color="warning"/>
    <Button icon="hourglass" color="danger"/>
    <Button icon="heart" color="primary" outlined/>
    <Button icon="hand" color="secondary" outlined/>
    <Button icon="address-book" color="success" outlined/>
    <Button icon="credit-card" color="info" outlined/>
    <Button icon="lemon" color="warning" outlined/>
    <Button icon="hourglass" color="danger" outlined/>
  </div>

  <h2 class="heading-2">Размер</h2>
  <div class="line">
    <Button label=".primary" color="primary" size="large"/>
    <Button label=".secondary" color="secondary" size="large"/>
    <Button label=".success" color="success" size="large"/>
    <Button label=".info" color="info" size="large"/>
    <Button label=".warning" color="warning" size="large"/>
    <Button label=".danger" color="danger" size="large"/>
  </div>
</template>
<style lang="scss" scoped>
.line {
  margin-bottom: 30px;
}

.heading-2{
  margin-bottom: 15px;
}
</style>