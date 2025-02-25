    <script setup>
    // Importando reactive
    import { reactive } from 'vue';

    // Estado reativo único
    const estado = reactive({
    // Definindo valores iniciais
    num1: 0,
    num2: 0,
    operation: '+'
    });

    // Função de cálculo pura
    const calcularResultado = () => {
    // Convertendo os inputs em números
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
        <!-- Divisão de inputs -->
        <div class="inputs">
            <!-- Inputs de entrada : Digitando o primeiro número -->
            <input type="number" v-model="estado.num1" placeholder="Primeiro número">
            <!-- Selecionando o operador -->
            <select v-model="estado.operation">
            <!-- Opções de operador -->
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">×</option>
            <option value="/">÷</option>
            </select>
            <!-- Inputs de entrada : Digitando o segundo número -->
            <input type="number" v-model="estado.num2" placeholder="Segundo número">
        </div>
        <!-- Divisão de resultados -->
        <div class="resultado">
        <h3>Resultado </h3>
        <!-- Exibindo o resultado -->
        <h3>{{ calcularResultado() }}</h3>
        </div>
    </div>
    </template>

    <style scoped>
    
    .calculadora {
     /* Centralizando a calculadora na tela */
     /* max-width: Definindo a largura máxima */
    max-width: 600px;
    /* margin: Definindo espaçamento externo */
    margin: 2rem auto;
    /* padding: Definindo espaçamento interno */
    padding: 2rem 1rem;
    /* background-color: Definindo cor de fundo */
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
    /* border-radius: Definindo raio de borda */
    border-radius: 8px;
    /* font-size: Definindo tamanho da fonte */
    font-size: 1.7rem;
    }

    .inputs {
    /* Definindo largura e centralizando os inputs */
    /* Display Flex: Alinhando os inputs */
    display: flex;
    /* Gap: Definindo espaçamento entre os inputs */
    gap: 0.5rem;
    /* Justify Content: Centralizando os inputs */
    justify-content: center;
    /* Align Items: Centralizando os inputs */
    margin: 2rem 0;
    }

    input, select {
    /*padding: Definindo espaçamento interno */
    padding: 0.8rem;
    /* font-size: Definindo tamanho da fonte */
    font-size: 1rem;
    /* border: Definindo borda */
    border: 1px solid #ddd;
    /* border-radius: Definindo raio de borda */
    border-radius: 4px;
    /* transition: Definindo transição */
    transition: border-color 0.3s ease;
    }
    /* Definindo estilo quando o input ou select estiver em foco */
    input:focus, select:focus {
    /* border-color: Definindo cor de borda */
    border-color: #42b983;
    /* outline: Definindo estilo de outline */
    outline: none;
    }

    /* Definindo estilo do resultado */
    .resultado {
    /*font-size: Definindo tamanho da fonte */
    font-size: 1.5rem;
    /* color: Definindo cor da fonte */
    color: #2c3e50;
    /*min-height: Definindo altura mínima */
    min-height: 2rem;
    }
    </style>