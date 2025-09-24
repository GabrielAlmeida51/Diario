## Aplicativo Diário Pessoal (Expo + Supabase)

### Tecnologias utilizadas

- React Native (Expo)
- Expo Router (navegação por arquivos)
- Supabase (Auth, Database, Storage)
- expo-image-picker (galeria/câmera)
- expo-av (áudio/vídeo) — com aviso de depreciação; pode migrar para expo-audio/expo-video
- TypeScript

### Passo a passo

1) Instalar dependências

```bash
npm install
```

2) Configurar Supabase (URL e KEY)

- Abra `app.json` e preencha:
  - `EXPO_PUBLIC_SUPABASE_URL`: cole a URL do seu projeto
  - `EXPO_PUBLIC_SUPABASE_ANON_KEY`: cole a Public anon key

3) Criar recursos no Supabase

- Abra o SQL Editor do Supabase e cole o conteúdo do arquivo `supabase.sql`. Execute para criar tabela, políticas (RLS) e gatilho.
- No Storage, crie um bucket chamado `journal-media`. Pode marcar como público para simplificar.

4) Rodar o app

```bash
npx expo start
```

### Funcionalidades implementadas

- Autenticação de usuário (login, cadastro, logout) com Supabase Auth
- Criação de entradas com título, conteúdo e upload de mídias (imagem/vídeo/áudio)
- Listagem das entradas do diário por usuário logado
- Visualização dos detalhes com renderização de imagem/vídeo/áudio
- Exclusão de entradas (e remoção dos arquivos do Storage)
- SQL pronto para criar tabela, políticas RLS e função RPC para inserção

5) Telas

- `app/index.tsx`: redireciona conforme sessão (login ou lista de entradas)
- `app/auth/index.tsx`: autenticação (Entrar/Criar conta)
- `app/entries/index.tsx`: lista entradas e botão Sair/Nova
- `app/entries/nova.tsx`: cria nova entrada com upload de mídia
- `app/entries/[id].tsx`: detalhe com exclusão

6) Código importante

- `lib/supabase.ts`: cliente com placeholders (URL/KEY)
- `lib/auth.ts`: helpers de sessão/login/logout
- `lib/storage.ts`: upload usando ArrayBuffer para o bucket `journal-media`

Tudo está em Português do Brasil.
