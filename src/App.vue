<script setup>
    import {reactive} from 'vue';

    const estado = reactive({
        valor1: 0,
        valor2: 0,
        filtro: 'somar'
    })

    const soma = function(){
        const {valor1, valor2} = estado;
        return (parseInt(valor1) + parseInt(valor2));
    }

    const diminui = function(){
        const {valor1, valor2} = estado;
        return (valor1 - valor2);
    }

    const multiplica = function(){
        const {valor1, valor2} = estado;
        return valor1 * valor2;
    }

    const divide = function(){
        const {valor1, valor2} = estado;
        return valor1 / valor2;
    }

    const retornaResultado = () => {
        const {filtro} = estado;
        switch(filtro){
            case 'somar':
                return soma();
            case 'subtrair':
                return diminui();
            case'multiplicar':
                return multiplica();
            case 'dividir':
                return divide();
            default:
                return 'Nada aqui';
        }
    }
</script>

<template>
    <div class="container">
        <div class="form">
                <div class="row">
                <h1>Calculadora Vue</h1>
            </div>
            <div class="row mt-3 mb-3">
                <div class="col-4">
                    <input :value="estado.valor1" @change="evento => estado.valor1 = evento.target.value" type="number" placeholder="Digite um número" class="form-control">
                </div>
            </div>
            <div class="row">
                <div class="col-4">
                    <input :value="estado.valor2" @change="evento => estado.valor2 = evento.target.value" type="number" placeholder="Digite um número" class="form-control">
                </div>
            </div>
            <div class="row mt-3">
                <div class="col-4">
                    <select @change="evento => estado.filtro = evento.target.value" class="form-control">
                        <option value="somar">Somar</option>
                        <option value="subtrair">Subtrair</option>
                        <option value="dividir">Dividir</option>
                        <option value="multiplicar">Multiplicar</option>
                    </select>
                </div>
            </div>
            <div class="row">
                <div class="col-4 mt-4">
                    <h4>Resultado: {{retornaResultado()}}</h4>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>

</style>
