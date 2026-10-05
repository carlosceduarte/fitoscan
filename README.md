# FitoScan

Protótipo web de triagem morfológica de folhas das 68 plantas medicinais da RENISUS, do TCC do MBA USP/Esalq (Pecege) sobre redes neurais convolucionais aplicadas à farmacobotânica.

## Estado atual

- Pré-processamento real da imagem: redimensionamento para 224 × 224, normalização ÷ 255 e as cinco variações de aumento de dados do método.
- Classificação em **modo demonstração**: as porcentagens vêm de um classificador simulado por forma da folha, sem pesos treinados. Não são resultado da CNN e não devem ser citadas como tal.
- Carrega um modelo Keras convertido para TensorFlow.js (`model.json` e arquivos `.bin`) pelo painel da etapa 3. As classes aceitas são só as da lista RENISUS.
- Comparação com fotos de referência: links de busca de imagens e comparação lado a lado.

## Rodar localmente

Abra `index.html` no navegador, ou, na pasta do projeto:

```
python3 -m http.server 8000
```

e acesse http://localhost:8000.

## Publicar com GitHub Pages

No repositório: Settings > Pages > Source: Deploy from a branch > Branch: `main`, pasta `/ (root)`. O endereço sai no formato `https://SEU_USUARIO.github.io/fitoscan/`.

## Próximos passos

1. Coletar imagens (GBIF, iNaturalist, speciesLink) e dividir treino, validação e teste por observação, não por foto.
2. Treinar com transferência de aprendizado (EfficientNetV2-B0 ou MobileNetV3) e avaliar com top-1, top-5 e matriz de confusão.
3. Exportar com `tensorflowjs_converter --input_format=keras modelo.h5 model/` e carregar o modelo direto da pasta `model/`.
4. Adicionar a classe "não reconhecida" para plantas fora da RENISUS.

Os dados de treino e os arquivos `.h5` ficam fora do repositório (ver `.gitignore`). Arquivos de modelo grandes (acima de 100 MB) pedem Git LFS ou uma release do GitHub.

## Fonte da lista de espécies

Relação Nacional de Plantas Medicinais de Interesse ao SUS (RENISUS), Ministério da Saúde.
