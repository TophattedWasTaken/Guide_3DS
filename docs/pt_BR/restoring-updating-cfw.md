# Restaurando / Atualizando CFW

## Leitura Obrigatória

Esta página prepara consoles com uma instalação moderna do boot9strap para reinstalação e/ou atualização de aplicativos de custom firmware. Ele também pode ser usado em caso de perda ou corrupção do cartão SD.

Seu cartão SD precisa estar formatado como FAT32 para seguir este guia, caso contrário, o 3DS não conseguirá reconhecê-lo. Se o seu cartão SD ainda não estiver formatado corretamente, use uma dessas páginas para formatá-lo, dependendo do seu sistema operacional: [Windows](formatting-sd-\(windows\)), [Mac](formatting-sd-\(mac\)), [Linux](formatting-sd-\(linux\)).

## O que é necessário

- A versão mais recente do [Luma3DS](https://github.com/LumaTeam/Luma3DS/releases/latest) (o arquivo `.zip` do Luma3DS)

## Instruções

1. Insira o cartão SD no seu computador
2. Copy everything from the Luma3DS `.zip` (`boot.firm`, `boot.3dsx`, and `config`) to the root of your SD card. If any of the files exist, overwrite them with the new files.
    - A raiz do cartão SD refere-se ao diretório inicial do seu cartão SD, onde você pode ver a pasta Nintendo 3DS, mas não está dentro dela
3. Reinsira o cartão SD no seu console
4. Ligue o seu console
    - Se você ver o menu de configuração do Luma3DS, pressione (Start) para salvar e reiniciar

::: info

A última versão do Luma3DS foi instalada no seu cartão SD e na memória interna.

:::

::: tip

Continue para [Finalizando a instalação](finalizing-setup) para instalar ou atualizar aplicativos homebrew (ex: FBI, Homebrew Launcher).

:::
