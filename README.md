# Sistema Solar em Realidade Aumentada

Aponte o celular para o marcador e o Sistema Solar aparece em cima dele, com os planetas orbitando o Sol. Toque em um astro para ver as informações dele.

Feito com **A-Frame** (cena 3D em HTML) e **MindAR** (rastreamento de imagem). Roda direto no navegador, sem instalar aplicativo.

## Arquivos

| Arquivo | Para que serve |
|---|---|
| `index.html` | O projeto inteiro: cena, planetas, texturas, painel e controles |
| `marcador.png` | A imagem que deve ser impressa ou mostrada em outra tela |
| `marcador.mind` | A "assinatura" do marcador que o MindAR usa para reconhecê-lo |

Os três precisam ficar na mesma pasta.

## O que o projeto faz

- Sol com brilho e iluminação real sobre os planetas (o lado oposto ao Sol fica escuro).
- Os 8 planetas orbitando em velocidades diferentes e girando em torno do próprio eixo.
- Vênus e Urano giram ao contrário, e o eixo de Urano é "deitado", como na realidade.
- A Lua orbitando a Terra, os anéis de Saturno, a Grande Mancha Vermelha de Júpiter e o cinturão de asteroides.
- Painel com diâmetro, distância do Sol, duração do ano, rotação, luas e uma curiosidade, com botões para navegar entre os astros.
- Controle de velocidade, botão de pausa e opção de mostrar ou esconder as linhas das órbitas.
- As texturas dos planetas são geradas por código, então não depende de baixar imagens.

## Como publicar e testar no celular (GitHub Pages)

O celular só libera a câmera em sites com **HTTPS**, por isso abrir o arquivo direto não funciona. O GitHub Pages resolve isso de graça:

1. Crie uma conta em github.com e um repositório novo (público).
2. Clique em **Add file › Upload files** e envie os três arquivos.
3. Vá em **Settings › Pages**, em *Branch* escolha `main` e a pasta `/ (root)`, e salve.
4. Em um ou dois minutos o site fica disponível em `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`.
5. Abra esse link no celular, permita a câmera e aponte para o `marcador.png` (impresso ou aberto na tela do computador).

Dica para a apresentação: gere um QR Code desse link e coloque-o no próprio pôster.

## Testar no computador

Com a webcam também funciona. Na pasta do projeto, rode um servidor local, por exemplo:

```
npx http-server
```

e abra `http://localhost:8080`. O `localhost` é aceito pelo navegador mesmo sem HTTPS. Mostre o marcador para a webcam pelo celular.

## Como usar seu próprio marcador

O marcador atual é a imagem de exemplo do MindAR. Para usar um pôster feito por vocês:

1. Crie a imagem. Ela precisa ter **muitos detalhes e contraste** (textos, desenhos, recortes). Imagens lisas, com degradê ou muito simétricas são difíceis de reconhecer.
2. Abra o compilador do MindAR: https://hiukim.github.io/mind-ar-js-doc/tools/compile
3. Envie a imagem, clique em *Start* e baixe o arquivo `targets.mind`.
4. Renomeie para `marcador.mind` e substitua o antigo (troque também o `marcador.png`, para ter a imagem certa à mão).

## Ajustes rápidos no código

Tudo fica no `index.html`:

- **Dados e informações dos planetas:** lista `ASTROS`, logo no início do script. Cada astro tem `raio`, `dist` (distância), `periodo` (segundos para dar uma volta no Sol), `giro` (rotação; número negativo gira ao contrário) e `inclinacao` (graus).
- **Tamanho do sistema em cima do marcador:** atributo `scale` da entidade `#sistema`.
- **Altura acima da imagem:** atributo `position` da entidade `#sistema`.
- **Usar fotos reais nas texturas:** troque `gerarTextura(p.id, ...)` pelo caminho de uma imagem, como `'texturas/terra.jpg'`. Texturas gratuitas: https://www.solarsystemscope.com/textures/

## Sobre a escala

Tamanhos, distâncias e tempos estão em **escala didática**. Na escala real, a Terra seria um pontinho invisível perto do Sol e Netuno ficaria dezenas de metros longe do marcador. Os números mostrados no painel, porém, são os reais. Vale comentar isso na apresentação.

O número de luas de Júpiter, Saturno e Urano muda com frequência, porque novas luas pequenas continuam sendo descobertas. Por isso o painel usa "mais de".

## Ideias para ir além

- Modo quiz ("toque no maior planeta").
- Narração em áudio ao tocar em cada planeta (componente `sound` do A-Frame).
- Botão para alternar entre escala didática e tamanhos proporcionais reais.
- Mais de um marcador: um com o Sistema Solar e outro com um planeta só, ampliado.
