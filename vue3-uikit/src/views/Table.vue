<script setup>
import { ref, computed } from 'vue'
import BaseTable from "@/components/Table/BaseTable.vue";
import TableRow from "@/components/Table/TableRow.vue";
import TableColumn from "@/components/Table/TableColumn.vue";
import Button from '@/components/Button.vue';

const tableHeads = ['Id', 'Author', 'Title', 'Cover', '']
const tableSizeColumns = '50px 1fr 2fr 150px 140px'

const sortField = ref('id')
const typeSort = ref('asc')

const books = ref([
  {
    id: 1,
    author: 'Dmitry Glukhovsky',
    title: 'Metro 2033',
    image: 'https://m.media-amazon.com/images/I/71SVz76COwL._AC_UF1000,1000_QL80_.jpg',
    bg: '#FFA26B'
  },
  {
    id: 12,
    author: 'James Clear',
    title: 'Atomic Habits: An Easy',
    image: 'https://m.media-amazon.com/images/P/0735211299.01._SCLZZZZZZZ_SX500_.jpg',
    bg: '#00C48C'
  },
  {
    id: 2,
    author: 'J. K. Rowling',
    title: 'Harry Potter and the Order of the Phoenix',
    image: 'https://m.media-amazon.com/images/I/51iQwWIl+XL.jpg',
    bg: '#00C48C'
  }
])

const bookSorting = computed(() => {
    return books.value.sort((a, b) => {
        let modifier = 1;
        if (typeSort.value === 'desc') modifier = -1
        if (a[sortField.value] < b[sortField.value]) return -1  * modifier
        if (a[sortField.value] > b[sortField.value]) return 1  * modifier
        return 0

    })
})

const setSort = (name) => {
    if (sortField.value === name) {
        if(typeSort.value === 'asc') {
            typeSort.value = 'desc'
        } else {
            typeSort.value = 'asc'
        }
    } else {
        sortField.value = name
    }
}
</script>
<template>
    <h1 class="heading-1">Таблица</h1>
    <div>Sort Field: {{ sortField }}</div>
    <div>Type Sort: {{ typeSort }}</div>
    <BaseTable
        :head="tableHeads"
        :columns-template="tableSizeColumns"
        @sorting="setSort">
        <TableRow
            v-for="book in bookSorting"
            :key="book.id"
            :columns-template="tableSizeColumns"
            :bg-row="book.bg">
            <TableColumn
                :column-title="tableHeads[0]">{{book.id}}</TableColumn>
            <TableColumn
                :column-title="tableHeads[1]">{{book.author}}</TableColumn>
            <TableColumn
                :column-title="tableHeads[2]">{{book.title}}</TableColumn>
            <TableColumn
                :image="true"
                :src-image="book.image"></TableColumn>
            <TableColumn>
                <Button label="Читать"/>
            </TableColumn>
        </TableRow>
    </BaseTable>  
</template>

