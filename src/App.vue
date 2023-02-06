<script setup>
import { ref, reactive } from 'vue';
const atividade = ref(null);
const descricao = ref(null);
const data = reactive([])
const input = ref(null);
function add() {
    data.push({
        atividade: atividade.value,
        descricao: descricao.value
    })
    atividade.value = ''
    descricao.value = ''
    input.value.focus()
}
function remove(value) {
    const index = data.findIndex(content => content === value)
    data.splice(index, 1);

}
</script>

<template>
    <div class="container">
        <label> Atividade:
            <input type="text" v-model="atividade" id="atividade" ref="input">
        </label>
        <label> Descrição:
            <textarea name="description" cols="30" rows="10" v-model="descricao" />
        </label>
        <button @click="add">add</button>
    </div>
    <template v-if="data.length > 0">
        <ul>
            <li v-for="value in data">{{ value.atividade }} - {{ value.descricao }} <button
                    @click="remove(value)">X</button></li>
        </ul>
    </template>
</template>

<style scoped>
.container {
    gap: 5px;
    display: flex;
    flex-direction: column;
}

label {
    display: flex;
    align-items: center;
    gap: 10px;
}

input {
    height: 30px;
    width: 200px;
}

textarea {
    width: 200px;
    height: 100px;
}

button {
    height: 30px;
    width: 100px;
}
</style>
