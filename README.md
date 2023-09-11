# Grid2D - Ambiente de Aprendizado por Reforço

## Visão Geral

O ambiente **Grid2D** é um ambiente de aprendizado por reforço inspirado no Grid World environment do livro de Reinforcement Learning de Sutton, capítulo 4. Projetado para testar e desenvolver algoritmos de aprendizado de máquina em tarefas de navegação em um ambiente 2D. Neste ambiente, um agente (anteriormente chamado de "agente") deve navegar por um grid 2D, evitar obstáculos e alcançar metas para maximizar sua recompensa total. O ambiente oferece suporte tanto à visão completa do ambiente quanto à visão parcial do agente.

## Regras do Cenário

As regras do cenário são as seguintes:

- O ambiente é representado como um grid 2D, onde o agente e outros elementos estão localizados.

- O agente (anteriormente chamado de "Agent") é representado por um quadrado azul.

- Existem três tipos de elementos no ambiente:
  1. **Objetivos (Goals)**: Representados por quadrados verdes. O agente deve alcançar os objetivos para receber uma recompensa positiva.
  2. **Fogo (Fire)**: Representado por quadrados vermelhos. Se o agente colidir com o fogo, ele receberá uma penalidade.
  3. **Espaço vazio (Empty Space)**: Áreas vazias representadas por espaços pretos no grid.

- O agente pode tomar quatro ações discretas:
  1. Mover para cima (0)
  2. Mover para baixo (1)
  3. Mover para a esquerda (2)
  4. Mover para a direita (3)

- O objetivo do agente é maximizar sua recompensa total, que é determinada pelas seguintes regras:
  - O agente recebe uma recompensa positiva quando alcança um objetivo (Goal).
  - O agente recebe uma penalidade quando colide com o fogo (Fire).
  - O agente recebe uma penalidade adicional se tentar sair dos limites do grid (bordas).

- O episódio termina quando o agente alcança um objetivo (recebe uma recompensa positiva) ou colide com o fogo (recebe uma penalidade).

## Uso do Ambiente

Para usar o ambiente Grid2D, siga estas etapas:

1. Importe o ambiente e crie uma instância:
   ```python
   from grid2d_env import Grid2DEnv

   env = Grid2DEnv(sizeX=10, sizeY=10)  # Substitua os tamanhos X e Y conforme necessário

2. Comece um episódio chamando o método reset():

   ```python
   state = env.reset()

3. No loop principal do seu algoritmo de aprendizado, escolha ações e execute-as chamando o método step(action):

   ```python
   action = env.action_space.sample()  # Substitua esta ação pela escolha do seu agente
   next_state, reward, done, _ = env.step(action)

4. Você pode renderizar a visão parcial do agente para fins de visualização:

    ```python
    partial_view = env.render(type='parcial', mode='human')

5. Continue o loop até que o episódio termine (quando done é True). O total da recompensa acumulada pode ser acessado durante ou após o episódio.

6. Ao final do episódio, você pode chamar env.close() para encerrar o ambiente.

## Personalização
Você pode personalizar o ambiente ajustando os tamanhos do grid, o número de objetivos e a disposição dos elementos no ambiente.

## Notas Adicionais
Este ambiente Grid2D pode ser útil para experimentar com algoritmos de aprendizado por reforço em cenários de navegação 2D. Sinta-se à vontade para adaptar e estender o ambiente para suas próprias necessidades e desafios de pesquisa em aprendizado de máquina.
