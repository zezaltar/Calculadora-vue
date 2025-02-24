    <script setup>
    import { reactive } from 'vue';

    // Estado reativo único
    const state = reactive({
    num1: 0,
    num2: 0,
    operation: '+'
    });

    // Função de cálculo pura
    const calcularResultado = () => {
    const a = Number(state.num1);
    const b = Number(state.num2);
    
    switch(state.operation) {
        case '+':
        return a + b;
        case '-':
        return a - b;
        case '*':
        return a * b;
        case '/':
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
        <input
            type="number"
            v-model="state.num1"
            placeholder="Primeiro número"
        >
        
        <select v-model="state.operation">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">×</option>
            <option value="/">÷</option>
        </select>

        <input
            type="number"
            v-model="state.num2"
            placeholder="Segundo número"
        >
        </div>

        <div class="result">
        <h2>Resultado: {{ calcularResultado() }}</h2>
        </div>
    </div>
    </template>

    <style scoped>
    .calculadora {
    max-width: 600px;
    margin: 2rem auto;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
    border-radius: 8px;
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

    .result {
    font-size: 1.5rem;
    color: #2c3e50;
    min-height: 2rem;
    }
    </style>