<script setup>
import { reactive } from 'vue';

const estado = reactive({
    num1: 0,
    num2: 0,
    operation: 'soma',
    result: 0
})

function fazAConta() {
    const { num1, num2, operation } = estado
    estado.result = num1, num2, operation

    switch (operation) {
        case 'soma':
            estado.result = num1 + num2;
            break
        case 'subtracao':
            estado.result = num1 - num2;
            break
        case 'multiplicacao':
            estado.result = num1 * num2;
            break
        case 'divisao':
            estado.result = num2 !== 0 ? num1 / num2 : 'Erro: Divisão por zero';
            break
        default:
            estado.result = 'Operação inválida'
    }
}

</script>

<template>
    <div class="mb-3">
        <div class="row">
            <div class="col-md-2">
                <input v-model="estado.num1" class="form-control" type="number" @input="fazAConta"
                    placeholder="Numero 1" id="number1">
            </div>
        </div>

        <div class="row mt-3 mb-3">
            <div class="col-md-2">
                <span>Sinal Aritmético: </span>
                <select v-model="estado.operation" class="form-control" @change="fazAConta" name="Sinais"
                    id="operation">
                    <option value="soma">+</option>
                    <option value="subtracao">-</option>
                    <option value="multiplicacao">*</option>
                    <option value="divisao">/</option>
                </select>
            </div>
        </div>

        <div class="row">
            <div class="col-md-2">
                <input v-model="estado.num2" class="form-control" type="number" @input="fazAConta"
                    placeholder="Numero 2" id="number2">
            </div>
        </div>
    </div>
    <h2>Resuldado: </h2>
    <span class="fs-2">{{ estado.result }}</span>
</template>