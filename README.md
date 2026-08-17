# PlaylistBridge

Importe playlists do YouTube direto para o Spotify, automaticamente - sem precisar instalar nada, sem backend, direto no navegador.

## Como funciona

1. Você cola o link de uma playlist do YouTube
2. O app busca as músicas via YouTube Data API v3
3. Você faz login no Spotify via OAuth 2.0 (PKCE)
4. O app pesquisa cada música no Spotify e cria a playlist automaticamente

## Pré-requisitos

Você vai precisar de duas chaves de API gratuitas:

**YouTube Data API v3**
- Acesse o [Google Cloud Console](https://console.cloud.google.com)
- Ative a YouTube Data API v3
- Crie uma chave de API

**Spotify Web API**
- Acesse o [Spotify for Developers](https://developer.spotify.com/dashboard)
- Crie um novo app
- Em Settings, marque **Web API** em "Which API/SDKs are you planning to use?"
- Adicione `http://127.0.0.1:5500/yt-to-spotify.html` como Redirect URI
- Copie o Client ID
- Em User Management, adicione o email da sua conta Spotify como usuário autorizado

## Como usar

1. Abra o arquivo `yt-to-spotify.html` no navegador (recomendado: via Live Server no VS Code na porta 5500)
2. Cole as chaves de API nos campos e clique em **Salvar configuração**
3. Clique em **Entrar com Spotify** e autorize o app
4. Cole o link da playlist do YouTube e clique em **Analisar playlist**
5. Clique em **Criar no Spotify**

## Observações

- As chaves de API ficam salvas apenas no `localStorage` do seu navegador - nada é enviado a servidores externos
- O app está em modo de desenvolvimento do Spotify, então só funciona para contas cadastradas em User Management (até 5 usuários)
- Músicas que não forem encontradas no Spotify serão marcadas como "não encontradas" e puladas
- O matching é feito por nome do canal + título do vídeo, com fallback só pelo título

## Stack

HTML + CSS + JavaScript puro, sem dependências externas ou build step.


Não preciso dizer o óbvio, isso aqui foi vibe coding.
