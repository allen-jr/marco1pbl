# Relatório

## 1. Introdução
O objetivo deste marco foi projetar, implementar em Verilog e validar através de simulação o hardware especializado para inferência de rede neural Extreme Learning Machine (ELM).

O sistema foi projetado para operar em ponto fixo Q4.12 , processando imagens de entrada de 28x28 pixels  de 784 bytes e fornecendo a classificação de dígitos de 0 a 9.

## 2. Levantamento de Requisitos e Especificação
Para o co-processador do Marco 1, foram levantados e implementados os seguintes requisitos:
- Arquitetura: O co-processador deve ter uma arquitetura sequencial, controlada por uma FSM.
- Datapath: Deve incluir unidades MAC (multiplica-acumula), ativação tanh aproximada via LUT e bloco Argmax final.
- Representação Numérica: Todos os cálculos e parâmetros de pesos e bias devem utilizar o formato de ponto fixo Q4.12.
- Armazenamento: Devem ser implementadas memórias (ROM/RAM) para a imagem de entrada (784 bytes) e para as matrizes de pesos e bias fornecidas.
- Interface: O hardware deve expor um conjunto de registradores para controle e monitoramento pela CPU (HPS), incluindo CTRL para START/RESET, STATUS para BUSY, DONE, ERROR, IMG para envio da imagem, RESULT para leitura do dígito predito e CYCLES para medição de desempenho.

## 3. Descrição da Solução de Hardware
