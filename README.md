# Detecção de encontros

Projeto em JavaScript e Node.js para identificar encontros a partir das posições dos monitorados.

## Como executar

Coloque os arquivos `.txt` na pasta `datasets` e rode, na pasta do projeto:

```bash
npm start
```

Os resultados são salvos em `outputs`. Também é possível escolher os arquivos:

```bash
node src/index.js dataset1.txt dataset2.txt
```

## Lógica

O programa lê os arquivos linha por linha. Os registros são agrupados pelo timestamp exato e os pares do mesmo horário são comparados. Os datasets devem estar ordenados por timestamp para que cada grupo possa ser processado assim que termina.

A distância é calculada pela fórmula de Haversine, usando raio terrestre de 6.371.000 metros. Distâncias menores que 20 metros são registradas. O tipo é `protetiva` quando há vínculo entre os IDs, `faccao` quando os dois pertencem à mesma facção e `generico` nos outros casos.

Escolhi essa abordagem porque separar a leitura, o cálculo e a detecção em funções deixa cada etapa mais simples de entender. A leitura linha por linha também permite processar arquivos grandes sem carregar o conteúdo inteiro na memória.
