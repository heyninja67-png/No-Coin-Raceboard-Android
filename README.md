# No Coin Raceboard — Android WebView

Aplicativo Android simples que abre o site **https://no-coin-raceboard.lovable.app/** em uma WebView nativa.

## Gerar o APK pelo GitHub Actions

1. Extraia este ZIP.
2. Crie um repositório no GitHub e envie **todo o conteúdo desta pasta** para a raiz do repositório.
3. Abra a aba **Actions** do repositório.
4. Se necessário, habilite GitHub Actions e selecione **Build No Coin Raceboard APK**.
5. Clique em **Run workflow**. Também haverá compilação automática quando houver push para `main` ou `master`.
6. Quando a execução ficar verde, abra a execução e baixe o artefato **no-coin-raceboard-debug-apk**.
7. Extraia o artefato e instale `app-debug.apk` no Android.

O APK gerado é de depuração (debug), assinado automaticamente para instalação e testes. Não é uma versão assinada para publicação na Google Play.

## O que já está configurado

- URL inicial do site definida em `MainActivity.java`.
- JavaScript, armazenamento DOM e cookies habilitados para compatibilidade com aplicações web modernas.
- Links HTTP/HTTPS e redirecionamentos de login mantidos dentro da WebView.
- Links como `mailto:`, `tel:` e outros esquemas encaminhados para aplicativos compatíveis.
- Botão de atualizar, barra de carregamento, botão voltar do Android e mensagem de erro com opção de tentar novamente.
- Seletor de arquivos para campos de upload da página.
- HTTPS obrigatório; conteúdo misto inseguro bloqueado.

## Requisitos

O build do GitHub Actions usa JDK 17, Gradle 8.9 e Android Gradle Plugin 8.7.3. O projeto compila com SDK 35 e suporta Android 6.0 (API 23) ou superior. Não é necessário instalar Android Studio no seu celular para gerar o APK pelo workflow.

## Observações importantes

- O aplicativo é um contêiner WebView: o conteúdo e os dados continuam sendo servidos pelo site. É necessária conexão com a internet.
- Alterações futuras no site aparecem no aplicativo sem recompilar o APK.
- Alguns provedores de autenticação podem bloquear login dentro de WebViews por política própria. O comportamento depende da configuração do site e do provedor de login.
- Este projeto não inclui servidor, banco de dados ou backend próprio; ele apenas abre o site informado.
