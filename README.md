## Projeto de Reconhecimento Facial com RetinaFace e MobileNetV2

### Introdução

Este projeto integra duas etapas fundamentais de visão computacional:

1. **Detecção de faces**, utilizando o modelo RetinaFace.
2. **Classificação de gênero (masculino/feminino)**, por meio de um classificador MobileNetV2 previamente treinado.

O objetivo principal é demonstrar como a combinação de detecção de objetos e classificação de imagens pode ser aplicada em um fluxo de trabalho prático e simples.

### Dataset

* **Fonte**: CelebA Dataset
* **Pré-processamento**:

  * Filtrei apenas as imagens rotuladas como **masculino** ou **feminino**.
  * Pré-processamento nas imagens para que ficassem no formato esperado pelo MobileNetV2.

### Metodologia

#### 1. Detecção de Faces com RetinaFace

* Instalamos e carregamos o `retinaface` para localizar regiões faciais em imagens.
* Para cada imagem de teste (uma foto de um homem e outra de uma mulher obtidas via Google Imagens):

  * Executei a detecção.
  * Desenhei caixas delimitadoras (`bounding boxes`) ao redor das faces detectadas.
  * Salvamos as imagens anotadas (com as caixas).

#### 2. Classificação de Gênero com MobileNetV2

* Utilizamos o `torchvision.models.mobilenet_v2` como arquitetura base.
* Ajustes realizados:

  * Adaptei a última camada para **duas classes**.
  * Treinei apenas por **10 épocas**.
  * Salvei os pesos finais do modelo em arquivo (`modelo_mobilenetv2.pth`).

### Resultados

Após a etapa de detecção, as imagens anotadas foram submetidas ao classificador:

* **Imagem do homem**: classificou como **masculino** com **72%** de confiança.
* **Imagem da mulher**: classificou como **feminino** com **82%** de confiança.

Esses resultados iniciais mostram que, mesmo com poucas épocas de treinamento, o modelo é capaz de diferenciar as duas classes com um nível de confiança promissor.

### Conclusão

Neste projeto aprendi um pipeline completo de detecção e classificação facial de forma simples, aprendi como a união das duas podem gerar grandes resultados.

---

