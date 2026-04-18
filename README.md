# Classificação de Gatos com PyTorch 🐈

Este é o meu primeiro projeto pessoal focado na construção e treinamento de uma Rede Neural Convolucional (CNN) utilizando PyTorch.

Ele atua como a primeira etapa de um projeto de robótica maior: o objetivo final é desenvolver um protótipo autônomo (utilizando hardwares como Raspberry Pi/ESP32-CAM) que consiga navegar pela casa, identificar meus gatos individualmente, interagir com eles e monitorar rotinas como a alimentação.

## Objetivo Atual (MVP)
Desenvolver um modelo de visão computacional capaz de classificar e distinguir corretamente imagens dos meus três gatos entre si, além de identificar gatos desconhecidos (intrusos).

## Os Objetos de Estudo
A arquitetura foi desenhada para extrair características visuais (textura de pelo, cores e padrões) de 4 classes distintas:

1. **MoonCake:** Pelagem branca, pelo longo, olhos azuis.S
2. **Francisco:** Pelagem rajada, pelo curto, olhos verdes.
3. **Pedrolino:** Pelagem frajola, pelo curto, variação de olhos verdes/amarelos.
4. **Desconhecidos:** Gatos de raças e cores variadas (classe de controle/anomalia).

## O Dataset e Pré-processamento
O dataset foi construído manualmente, totalizando cerca de 587 imagens, com forte presença de ruído orgânico (diferentes iluminações, fundos complexos e oclusões).

O *pipeline* de dados foi construído com `torchvision.transforms` para padronizar as entradas da rede:
* `Resize(256)` e `CenterCrop(224)` para garantir matrizes quadradas perfeitas sem distorcer as texturas das pelagens.
* `ToTensor()` e `Normalize()` utilizando os padrões do ImageNet para otimização do gradiente descendente.
* Separação de 80% dos dados para Treino e 20% para Validação, processados em `batches` de 32 imagens para preservação de memória da GPU.

## Tecnologias Utilizadas
* **Linguagem:** Python
* **Framework:** PyTorch & Torchvision
* **Ambiente:** Google Colab
* **Manipulação de Dados:** PyTorch DataLoader

## Próximos Passos
- [x] Coleta e estruturação do Dataset.
- [x] Pipeline de pré-processamento (Transforms & DataLoaders).
- [ ] Construção da arquitetura da CNN (Baseline vs. Transfer Learning com EfficientNet).
- [ ] Desenvolvimento do Loop de Treinamento (Otimizadores e Funções de Perda).
- [ ] Validação gráfica (Acurácia vs. Loss) para combate ao Overfitting.
- [ ] Script de inferência isolado executando os pesos do melhor modelo salvo.