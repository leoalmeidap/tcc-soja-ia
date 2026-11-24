# TCC Soja IA

Classificação de ferrugem asiática e mancha-alvo em folhas de soja por rede neural convolucional: estimativa exploratória de severidade.

Leonardo de Almeida Pereira — Engenharia Agronômica, Universidade de Sorocaba (UNISO), 2026. Orientadora: Kelen Cristiane Cardoso.

## Código e proveniência
`TCC_SOJA_IA.ipynb` contém as 85 células do notebook original exportado do Google Colab. O conteúdo das células foi preservado; saídas de execução e metadados não essenciais foram removidos para publicação. O notebook não foi reexecutado na preparação deste pacote.

## Dados
ASDID — Auburn Soybean Disease Image Dataset: https://doi.org/10.5061/dryad.41ns1rnj3 . A seleção experimental contém 900 imagens para desenvolvimento (300 por classe) e 60 para teste (20 por classe). Imagens e pesos treinados não acompanham este pacote. Para reproduzir fielmente os resultados, é necessário recuperar a seleção original e o ambiente correspondente; baixar o banco por si só não garante a mesma seleção.

## Estrutura no Drive
```
MyDrive/TCC_Soja_IA/
  dataset/
    Saudavel/
    Ferrugem/
    Mancha_Alvo/
  teste/
    Saudavel/
    Ferrugem/
    Mancha_Alvo/
  resultados/
```

## Execução
Abra o notebook no Google Colab, ative uma GPU se disponível, monte o Drive e confira a estrutura acima. Crie a pasta resultados se necessário. Execute as células na ordem, em uma cópia de trabalho: o notebook inclui treinamento e salvamento de arquivos e pode sobrescrever resultados se executado sobre a pasta original. TensorFlow 2.20.0 foi registrado na execução original; as versões das demais bibliotecas não foram confirmadas. As dependências estão listadas em requirements.txt. A instalação não reproduz necessariamente o ambiente histórico.

Parâmetros: imagens 224 × 224, lote 32, semente 42 para divisão, 80% treino e 20% validação, EfficientNetB0 com pesos ImageNet e base congelada, Adam 0,001, dropout 0,30, 20 épocas. Ordem das classes do classificador: Ferrugem, Mancha_Alvo, Saudavel. Limiar final da severidade: 0,38.

## Resultados documentados
Acurácia no teste: 95,0% (57/60). Médias exploratórias de severidade: ferrugem 31,75%, mancha-alvo 69,63%, saudável 30,91%. A estimativa de severidade não foi validada quantitativamente, apresentou falsos positivos e alertas de segmentação em todas as 20 imagens de mancha-alvo. Imagens do teste foram visualizadas durante testes exploratórios de severidade. Não há comprovação de desempenho em campo.

## Divulgação
Confirme a autorização de publicação e a licença com a orientadora antes de tornar o repositório público. Não redistribua imagens do ASDID sem verificar as condições de uso. O título acima deve ser atualizado caso seja alterado na versão aprovada do TCC.
