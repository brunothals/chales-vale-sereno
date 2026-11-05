# Chalés Vale Sereno — protótipo do app de reservas

Tudo está em **um único arquivo**: `index.html`. As fotos já estão embutidas dentro dele,
então você pode mandar só esse arquivo por WhatsApp/Drive e abrir direto no celular.

## Como abrir no celular
- **Android:** envie o `index.html` por WhatsApp ou Drive, baixe e abra com o Chrome.
- **iPhone:** salve o arquivo nos Arquivos e toque nele (abre no Safari). Se abrir como texto,
  hospede o arquivo em qualquer lugar gratuito (Netlify Drop, Vercel, GitHub Pages) e mande o link.
- No computador ele aparece dentro de uma moldura de celular, bom para apresentar na tela.

## Antes de mostrar: coloque seu WhatsApp
Abra o `index.html` em um editor de texto (Bloco de Notas serve), procure `CONFIG` e troque:

```js
whatsappBruno: '55XXXXXXXXXXX',   // ex.: '5535999999999' (DDI 55 + DDD + número)
```

É esse número que o botão **"Quero meu app de reservas"** (aba *Seu app*) chama.

## Painel do dono (a tela que mais vende)
Na tela inicial, **toque 3 vezes no logo** no canto superior esquerdo.
Também há um link discreto "Área do proprietário" no fim da aba *Seu app*.

## Trocar nomes dos chalés, descrições e fotos
No mesmo arquivo, procure `const CHALES`. Cada linha é um chalé:

```js
{id:'araucaria', nome:'Chalé Araucária', dif:'lareira', fotos:['hero-chale','kitchenette','vista'], desc:'...'},
```

- `nome` e `desc`: edite à vontade.
- `dif`: use `'lareira'` ou `'banheira'` (muda o ícone, o selo e o texto).
- `fotos`: lista de chaves da tabela `FOTOS` (a primeira é a capa do card).

## Trocar fotos
Procure `const FOTOS`. Cada chave aponta para uma foto embutida (um texto enorme começando com
`data:image/webp;base64,...`). Para trocar, substitua esse texto pelo caminho de um arquivo
ao lado do `index.html`:

```js
'piscina': 'fotos/piscina-nova.jpg',
```

A pasta `fotos/` já vem com as 12 fotos tratadas, para referência. Se usar caminhos de arquivo,
lembre de enviar a pasta junto (ou hospedar tudo). Com as fotos embutidas, o arquivo sozinho basta.

Fotos usadas: `hero-chale` (tela inicial), `chale-fachada`, `chales`, `vista`, `piscina`,
`piscina-noite`, `fogueira`, `lareira`, `kitchenette`, `banheiro`, `cafe`, `cafe-bolo`.

## Trocar preços (tudo marcado como exemplo)
Em `CONFIG`:

```js
diariaBase: 379,        // segunda a quinta
diariaFimSemana: 429,   // sexta e sábado
diariaAlta: 489,        // julho e dezembro
sinal: 0.30,            // 30% de sinal via Pix
```

Os valores dos extras (kit romântico, decoração) ficam em `const XP`.
Os preços também podem ser alterados ao vivo no **Painel do dono** durante a apresentação.

## O que é simulado
- Disponibilidade do calendário, ocupação, receita e "reservas do dia" são geradas automaticamente
  e mudam conforme o mês atual. Nada é salvo: ao recarregar, volta ao estado inicial.
- O QR code Pix é fictício e traz o carimbo "DEMONSTRAÇÃO".
- Avaliações exibidas são só as reais informadas: 9,5 no Booking (107 avaliações) e 4,8 no Google.
