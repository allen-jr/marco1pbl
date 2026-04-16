# Relatório

## 1. Levantamento de Requisitos

O sistema desenvolvido tem como objetivo a implementação de um co-processador em FPGA capaz de realizar a inferência de uma rede neural do tipo Extreme Learning Machine (ELM). Esse co-processador deve ser responsável por classificar imagens de dígitos numéricos de 0 a 9 representadas em escala de cinza, com dimensão de 28×28 pixels, totalizando 784 valores de entrada.

Para atender a esse objetivo, o sistema precisa implementar corretamente as etapas da inferência da ELM, incluindo a leitura do vetor de entrada, o processamento da camada oculta por meio de operações de multiplicação e acumulação, a aplicação de uma função de ativação aproximada, o cálculo da camada de saída e, por fim, a determinação da predição por meio da operação de argmax. Além disso, o projeto deve utilizar representação em ponto fixo no formato Q4.12.

Outro requisito fundamental é a organização da arquitetura em dois blocos principais: um datapath responsável pelas operações aritméticas e uma unidade de controle implementada como uma máquina de estados finitos (FSM). Também é necessário o uso de memórias internas para armazenamento da imagem de entrada, pesos e bias da rede, podendo ser implementadas por meio de ROM inicializada com arquivos .mif. Por fim, o sistema deve ser capaz de ser validado por meio de simulação, utilizando vetores de teste fornecidos e comparando os resultados com um modelo de referência.

## 2. Detalhamento dos Softwares Utilizados

O desenvolvimento do projeto foi realizado utilizando o software Intel Quartus Prime Lite Edition, ferramenta responsável pela síntese, análise, compilação e geração do arquivo de configuração da FPGA. Essa ferramenta também foi utilizada para integração dos módulos em Verilog e verificação estrutural do projeto.

Além disso, foram utilizados recursos do próprio Quartus para criação e manipulação de memórias inicializadas por arquivos .mif, que armazenam os pesos, bias e dados de entrada. Para a validação do sistema, foi utilizado um testbench em Verilog, permitindo simular o funcionamento do co-processador antes da implementação em hardware. O ambiente de desenvolvimento foi executado em sistema operacional Linux.

## 3. Especificação dos Hardwares Utilizados

Os testes do projeto foram realizados utilizando a plataforma DE1-SoC. Essa plataforma integra um sistema heterogêneo composto por um processador ARM (HPS) e a lógica programável da FPGA, permitindo futura integração com software.

## 4. Instalação e Configuração do Ambiente

O processo de desenvolvimento do sistema iniciou-se com a criação de um novo projeto no Quartus, no qual foram adicionados os arquivos em Verilog correspondentes ao datapath, à unidade de controle e aos demais módulos auxiliares.

Em seguida, foram incluídos os arquivos de memória no formato .mif, utilizados para armazenar os parâmetros da rede neural, como pesos e bias. Esses arquivos foram associados às memórias internas do projeto por meio de inferência.

Após a organização dos arquivos, foi realizada a compilação completa do projeto, incluindo análise, síntese e mapeamento. Para a validação, foi desenvolvido um testbench que permite simular o comportamento do sistema, verificando a correta execução das etapas da inferência.

## 5. Testes de Funcionamento e Manutenção

Os testes de funcionamento foram realizados por meio de simulação utilizando testbench em Verilog. Foram utilizados vetores de teste fornecidos, representando imagens e parâmetros da rede neural, com o objetivo de validar a saída do sistema em relação a um modelo de referência.

Durante os testes, o sistema foi submetido a diferentes entradas, verificando-se o comportamento das etapas de processamento da ELM, incluindo a operação do bloco de multiplicação e acumulação, a aplicação da função de ativação e o cálculo do argmax. A saída gerada pelo sistema foi comparada com os valores esperados, garantindo a correção da implementação.

Nessa fase, foram identificados problemas relacionados aos blocos de multiplicação e acumulação (MAC) e ao cálculo do argmax. Esses problemas ocasionavam a repetição de um mesmo valor de saída na placa, independentemente da entrada fornecida. Após análise, verificou-se que esse comportamento estava associado ao fato de que determinadas estruturas de memória e registradores não estavam sendo devidamente reinicializados entre execuções, o que fazia com que valores anteriores permanecessem armazenados e influenciassem os resultados subsequentes.

A correção foi realizada por meio do ajuste na lógica de controle, garantindo a limpeza adequada dos registradores e memórias utilizadas durante o processamento, além de revisões no fluxo de operação do MAC e do bloco de argmax. Após essas modificações, o sistema passou a apresentar comportamento consistente, com saídas variando corretamente de acordo com as entradas fornecidas.

## 6. Análise dos resultados alcançados

Os resultados obtidos demonstraram que o co-processador implementado foi capaz de realizar 
corretamente as etapas da inferência da rede neural ELM, produzindo saídas compatíveis com o modelo de referência utilizado nos testes. A separação entre datapath e unidade de controle contribuiu para uma organização clara do projeto e facilitou o desenvolvimento.

O uso de representação em ponto fixo permitiu a execução eficiente das operações aritméticas na FPGA. A utilização de memórias inicializadas por arquivos .mif também se mostrou adequada para armazenar os parâmetros da rede.

De modo geral, o sistema atendeu aos requisitos estabelecidos para o Marco 1, apresentando funcionamento estável após as correções realizadas. O projeto estabelece uma base sólida para as próximas etapas, que envolvem a integração com o sistema operacional Linux e o desenvolvimento da aplicação em linguagem C.
