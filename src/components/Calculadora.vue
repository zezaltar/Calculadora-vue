    <script setup>
    import { reactive } from 'vue';

    // Estado reativo único
    const estado = reactive({
    num1: 0,
    num2: 0,
    operation: '+'
    });

    // Função de cálculo pura
    const calcularResultado = () => {
    const a = Number(estado.num1);
    const b = Number(estado.num2);
    
    // Escolhendo o operador
    switch(estado.operation) {
        //Caso o operador seja '+'
        case '+':
        //Soma os dois números
        return a + b;
        //Caso o operador seja '-'
        case '-':
        //Subtrai os dois números
        return a - b;
        //Caso o operador seja '*'
        case '*':
        //Multiplica os dois números
        return a * b;
        //Caso o operador seja '/'
        case '/':
        //Divide os dois números e verifica se b é zero
        return b !== 0 ? a / b : 'Erro: Divisão por zero';
        default:
        return 0;
    }
    };
    </script>

    <template>
    <div class="calculadora">
        <h1>Calculadora Aritmética</h1>
        <div class="inputs">
            <!-- Inputs de entrada : Digitando o primeiro número -->
            <input type="number" v-model="estado.num1" placeholder="Primeiro número">
            <!-- Selecionando o operador -->
            <select v-model="estado.operation">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">×</option>
            <option value="/">÷</option>
            </select>
            <!-- Inputs de entrada : Digitando o segundo número -->
            <input type="number" v-model="estado.num2" placeholder="Segundo número">
        </div>

        <div class="resultado">
        <h3>Resultado </h3>
        <h3>{{ calcularResultado() }}</h3>
        </div>
    </div>
    </template>

    <style scoped>
    
    .calculadora {
    max-width: 600px;
    margin: 2rem auto;
    padding: 2rem 1rem;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
    border-radius: 8px;
    font-size: 1.7rem;
    }

    .inputs {
    display: flex;
    gap: 0.5rem;
    justify-content: center;
    margin: 2rem 0;
    }

    input, select {
    padding: 0.8rem;
    font-size: 1rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    transition: border-color 0.3s ease;
    }

    input:focus, select:focus {
    border-color: #42b983;
    outline: none;
    }

    .resultado {
    font-size: 1.5rem;
    color: #2c3e50;
    min-height: 2rem;
    }
    </style>