<script setup>
import { ref } from 'vue'
import Tabs from '@/components/Tabs.vue'

const tabs = [
    {name:'First', label: 'Lorem5'},
    {name:'Second', label: 'Lorem10'},
    {name:'Third', label: 'Lorem15'},
]
const selectedTab = ref('Second')

const changeTab = (tabName) => {
    selectedTab.value = tabName
}
</script>
<template>
    <h1 class="heading-1">Табы</h1>
    <Tabs
        :names="tabs"
        :selectedTab="selectedTab"
        @changeTab="changeTab">
        <div v-if="selectedTab === 'First'">Lorem ipsum dolor sit amet.</div>
        <div v-if="selectedTab === 'Second'">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Tempore, unde.</div>
        <div v-if="selectedTab === 'Third'">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Facilis perferendis fugit exercitationem nulla officiis ex?</div>
    </Tabs>
</template>

<style lang="scss" >
    
</style>