# Árvore de Steiner Euclidiana - Têmpera Simulada

## Disciplina: Projeto e Análise de Algoritmos 4062/01 - 2024

### Discentes: Sergio Alvarez, Jean Martins

---

## Introdução

Este projeto implementa uma abordagem para encontrar a **Árvore Geradora Mínima (MST)** para um conjunto de pontos, com a possibilidade de adicionar pontos de **Steiner** para otimização adicional. O projeto utiliza uma combinação do algoritmo de Kruskal e do método de **Tempera Simulada** (Simulated Annealing) para encontrar uma solução que minimiza o comprimento total da árvore.

## Como Usar

### Requisitos

Certifique-se de ter os seguintes pacotes instalados:

- `numpy`
- `scipy`
- `matplotlib`

### Execução

1. **Defina os pontos terminais**:

   - Os pontos terminais são definidos no início do código. Por padrão, eles são definidos como os vértices de um triângulo:
     ```python
     terminals = np.array([[0, 1], [1, 1], [0.5, 1 - np.sqrt(3)/2]])
     ```
   - Você pode substituir esses pontos por qualquer conjunto de coordenadas que desejar.

2. **Parâmetros da Tempera Simulada**:

   - Os parâmetros para o algoritmo de Tempera Simulada, como a temperatura inicial, a taxa de resfriamento e o número máximo de iterações, são configuráveis:
     ```python
     num_steiner_points = 2
     initial_temp = 5
     cooling_rate = 0.99
     max_iterations = 100000
     ```

3. **Geração da Solução Inicial**:

   - A função `initial_solution` é chamada para gerar e plotar a solução inicial baseada na MST dos pontos terminais.

4. **Execução do Algoritmo de Tempera Simulada**:
   - A função `simulated_annealing` é utilizada para executar o processo de otimização e encontrar a melhor MST possível.

### Plotagem e Resultados

O código gera gráficos que mostram a evolução da solução ao longo do tempo, incluindo:

- A solução atual, a melhor solução atual e a melhor solução geral em um gráfico comparativo.
- O histórico de aceitação do algoritmo de Tempera Simulada, mostrando como a temperatura e o comprimento da MST variam ao longo das iterações.

Os gráficos são salvos na pasta `plots` e podem ser visualizados para entender o processo de otimização.

### Execução Completa

Para executar o código completo, certifique-se de que o ambiente de execução tenha acesso a todos os pacotes necessários e simplesmente execute o script Python. O código salvará os resultados na pasta `plots` e exibirá os gráficos no final da execução.

### Exemplo de Uso

Abaixo está um exemplo básico de como configurar e executar o script:

```python
if __name__ == "__main__":
    if not os.path.exists('plots'):
        os.makedirs('plots')
    terminals = np.array([[0, 1], [1, 1], [0.5, 1 - np.sqrt(3)/2]])
    plot_terminals(terminals)
    num_steiner_points = 2
    initial_temp = 5
    cooling_rate = 0.99
    max_iterations = 100000
    initial_points, initial_connections = initial_solution(terminals, num_steiner_points)
    initial_length = calculate_tree_length(initial_points, initial_connections)
    print(f'Comprimento inicial: {initial_length}')
    print(f'Pontos iniciais: {initial_points}')
    print(f'Conexões iniciais: {initial_connections}')
    best_points, best_connections, best_length = simulated_annealing(terminals, num_steiner_points, initial_temp, cooling_rate, max_iterations, record_interations=False)
```
