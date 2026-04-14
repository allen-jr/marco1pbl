# Relatório

## 1. Definição do Problema
Este projeto tem como objetivo implementar, em FPGA, um coprocessador capaz de classificar dígitos de 0 a 9 a partir de imagens em escala de cinza de tamanho 28×8. O sistema realiza a inferência utilizando uma rede neural do tipo Extreme Learning Machine (ELM).

A implementação foi desenvolvida em Verilog, adotando uma arquitetura sequencial composta por um datapath e uma máquina de estados finitos (FSM) para controle. Os dados são representados em ponto fixo no formato Q4.12.

Neste marco, o foco está na construção do hardware e na validação do seu funcionamento por meio de simulações.

## 2. Fundamentação Teórica

### 2.1. Extreme Learning Machine
A ELM é uma rede neural com apenas uma camada oculta. O processamento ocorre em etapas: inicialmente, calcula-se a saída da camada oculta a partir da entrada; em seguida, é feita a computação da camada de saída; por fim, seleciona-se o maior valor (argmax), que corresponde ao dígito previsto.

### 2.2. Representação em Ponto Fixo (Q4.12)
Os valores são representados com 16 bits no formato Q4.12, sendo 4 bits para a parte inteira e 12 bits para a parte fracionária. Essa abordagem é mais eficiente para implementação em FPGA do que o uso de ponto flutuante, pois consome menos recursos de hardware e permite maior desempenho.

### 2.3. Arquitetura de Hardware
O sistema foi dividido em duas partes principais: o datapath, responsável pelos cálculos, e a FSM, que controla a sequência das operações. Essa separação facilita o desenvolvimento do projeto e melhora a organização do código.

## 3. Descrição da Solução

### 3.1. Visão Geral da Arquitetura

### 3.2. Diagrama de Blocos

### 3.3. FSM de Controle

### 3.4. Datapath

### 3.5. Função de Ativação

### 3.6. Argmax

### 3.7. Memórias

### 3.8. Banco de Registradores

## 4. Metodologia de Testes


## 5. Resulatdos

## 6. Ambiente de Desenvolvimento

## 8. Instalação e Configuração de Ambiente
