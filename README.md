# Visualizador de Imagens (Android)

App offline para ver fotos do aparelho: galeria, zoom (pinça e toque duplo),
girar, deslizar para trocar e apresentação. As imagens nunca saem do aparelho.

Para testar rápido no computador, abra `www/index.html` no navegador.

## Antes de tudo
Em `capacitor.config.json`, troque `appId` por um identificador seu
(ex.: `com.joaosilva.visualizador`). Depois de publicado, ele não deve mudar.

## Caminho A: gerar o APK sem instalar nada (recomendado)
1. Crie um repositório no GitHub e envie esta pasta inteira.
2. Abra a aba **Actions** > **Gerar APK** > **Run workflow**.
3. Quando terminar (uns 5 min), baixe `visualizador-apk` em **Artifacts**.
   Dentro do zip está o `app-debug.apk`.

## Caminho B: gerar no seu computador
Requisitos: Node 18+ e JDK 17 (ou Android Studio).

    npm install
    npx cap add android
    npx cap sync android
    cd android && ./gradlew assembleDebug

O APK fica em `android/app/build/outputs/apk/debug/app-debug.apk`.

## Distribuir
- **Instalação direta (WhatsApp, site, pendrive):** o `app-debug.apk` já
  funciona. Quem instalar precisa permitir "fontes desconhecidas".
- **Google Play:** exige um app assinado em formato AAB. Gere uma chave com
  `keytool -genkey -v -keystore minha.keystore -alias app -keyalg RSA -keysize 2048 -validity 10000`,
  guarde-a em local seguro (sem ela você não atualiza o app) e use no Android Studio:
  **Build > Generate Signed Bundle / APK**.
