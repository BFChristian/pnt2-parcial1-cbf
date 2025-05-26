<template>
    <form>
        <h1>NT2 - Parcial</h1>
        <input type="text" v-model.trim="textoIngresado" placeholder="Ingresar un texto" />
        <p>cantidad caracteres = {{ informacionTexto.cantidad }}</p>
    </form>
    <div id="representaciones">
        <h3>Representaciones</h3>
        <p>1 - {{ codificado }} (Codificado)</p>
        <p>2 - {{ this.textoIngresado.toUpperCase() }} (mayuscula)</p>
        <p>3 - {{ this.textoIngresado.toLowerCase() }} (minuscula)</p>
        <p>4 - {{ intercalarMayusculaMinuscula(this.textoIngresado) }}(mayuscula/minuscula)</p>
        <p>5 - {{ intercalarMinusculaMayuscula(this.textoIngresado) }}(minuscula/mayuscula)</p>
    </div>
    <hr>
    <h2>Preguntas</h2>
    <p>Pregunta 1: C</p>
    <p>Pregunta 2: C</p>
    <p>Pregunta 3: A</p>
</template>

<script>
export default {
    name: 'Formulario',
    props: [],
    data() {
        return {
            textoIngresado: '',
        }
    },
    methods: {
        intercalarMinusculaMayuscula(texto) {
            let resultado = '';
            for (let i = 0; i < texto.length; i++) {
                if (i % 2 === 0) {
                    resultado += texto[i].toLowerCase();
                } else {
                    resultado += texto[i].toUpperCase();
                }
            }
            return resultado;
        },
        intercalarMayusculaMinuscula(texto) {
            let resultado = '';
            for (let i = 0; i < texto.length; i++) {
                if (i % 2 === 0) {
                    resultado += texto[i].toUpperCase();
                } else {
                    resultado += texto[i].toLowerCase();
                }
            }
            return resultado;
        }
    },
    computed: {
        informacionTexto() {
            return {
                cantidad: this.textoIngresado.length
            }
        },
        codificado() {
            return this.textoIngresado.toLowerCase().replace(/a/g, "u").replace(/e/g, "o").replace(/o/g, "e").replace(/u/g, "a");
        }
    },
}
</script>

<style scoped></style>