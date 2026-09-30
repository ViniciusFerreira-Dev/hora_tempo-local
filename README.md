# Hora e tempo local

Página simples, feita só com HTML, CSS e JavaScript, que mostra a hora, o tempo e os feriados do lugar onde a pessoa está.

## O que a página faz

- **Hora local:** relógio atualizado a cada segundo, com o fuso do dispositivo.
- **Tempo agora:** temperatura, sensação térmica, umidade, vento, nascer e pôr do sol da cidade.
- **Previsão de 6 dias:** máxima, mínima e chance de chuva de cada dia.
- **°C e °F:** botão para alternar a unidade. A escolha fica salva no navegador.
- **Fundo que segue o tempo:** a cor muda conforme o clima (limpo, nublado, chuva, trovoada, neve) e se é dia ou noite.
- **Calendário com feriados:** feriados nacionais, estaduais e municipais, além de pontos facultativos, conforme o local da pessoa.

## Como funciona

1. O navegador pede a localização da pessoa. Se ela negar, a página usa a cidade do fuso horário como aproximação.
2. Com as coordenadas, a página consulta APIs gratuitas e sem chave:
   - [Open-Meteo](https://open-meteo.com/) para o tempo, a previsão e o nascer e pôr do sol;
   - [BigDataCloud](https://www.bigdatacloud.com/) para descobrir cidade, estado e país;
   - [Nager.Date](https://date.nager.at/) para os feriados (com a [BrasilAPI](https://brasilapi.com.br/) como reserva no Brasil).
3. Os pontos facultativos móveis do Brasil (Carnaval, Quarta-feira de Cinzas e Corpus Christi) são calculados a partir da data da Páscoa.

## Como rodar no seu computador

A geolocalização só funciona em `https://` ou em `localhost`. Abrir o arquivo com duplo clique pode falhar. Na pasta do projeto, rode:

```bash
python -m http.server 8000
```

Depois abra `http://localhost:8000` no navegador.

## Como adicionar feriados da sua cidade

Os feriados estaduais e municipais ficam na lista `LOCAL_HOLIDAYS`, no início do bloco de calendário do `index.html`. Exemplo:

```js
{ country: 'BR', state: 'Bahia', city: 'Juazeiro', date: '07-05', name: 'Nome do feriado', type: 'Municipal' }
```

- `date: 'MM-DD'` repete todo ano.
- `date: 'AAAA-MM-DD'` vale só naquele ano (útil para pontos facultativos, que mudam a cada decreto). Nesse caso, use `type: 'Ponto facultativo'`.

Hoje a lista inclui os feriados estaduais de Pernambuco e os municipais de Petrolina, conferidos no calendário oficial da Prefeitura de 2026.

## Tecnologias

HTML, CSS e JavaScript puros, sem bibliotecas nem etapa de build. A fonte é a IBM Plex Sans, carregada do Google Fonts.

## Autor

Vinicius Ferreira Costa Silva: [LinkedIn](https://linkedin.com/in/vinicius-ferreira-32b734185)
