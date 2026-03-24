# POKEpok

POKEpok é um site em HTML que permite rodar jogos de Game Boy Advance diretamente no navegador utilizando um emulador web. O projeto foi feito com foco em simplicidade, desempenho e salvamento local automático, sem necessidade de servidor ou backend.

## Visão geral

O site funciona como um launcher de ROMs `.gba`, permitindo que o usuário carregue um arquivo local e jogue imediatamente em tela cheia. Todo o progresso é salvo no `localStorage` do navegador, garantindo continuidade mesmo após fechar a página.

## Funcionalidades

- Execução de ROMs de Game Boy Advance no navegador
- Interface moderna com animações e transições suaves
- Tela de introdução personalizada
- Modo tela cheia automático
- Salvamento automático de estado (save state)
- Salvamento interno do jogo (save file)
- Recuperação automática de progresso
- Suporte a múltiplas ROMs com identificação única
- Carregamento de arquivos locais (`.gba`, `.agb`, `.bin`, `.zip`, `.7z`)

## Como funciona

O sistema utiliza o EmulatorJS com o core mGBA carregado via CDN. Quando o usuário seleciona uma ROM:

1. O arquivo é processado no navegador
2. Um identificador único é gerado usando hash SHA-256
3. O jogo é carregado via URL temporária (Blob URL)
4. Saves e estados são armazenados no localStorage em base64
5. Ao reabrir a mesma ROM, o progresso é restaurado automaticamente

## Estrutura

O projeto é composto por um único arquivo HTML contendo:

- Estilização completa em CSS (sem dependências externas)
- Interface com launcher e overlay
- Sistema de gerenciamento de arquivos locais
- Integração com EmulatorJS
- Persistência de dados via localStorage

## Salvamento

O sistema utiliza duas formas de persistência:

- **State Save**: estado completo do emulador
- **Save File**: progresso interno do jogo

Ambos são convertidos para base64 e armazenados com uma chave única baseada no arquivo da ROM.

## Controles

Os controles seguem o padrão do emulador mGBA:

- Teclado padrão (setas, Z, X, Enter, Shift)
- Suporte a controle dependendo do navegador

## Como usar

1. Abra o arquivo HTML no navegador
2. Clique em "Carregar ROM"
3. Selecione um arquivo `.gba`
4. O jogo iniciará automaticamente
5. O progresso será salvo automaticamente

## Requisitos

- Navegador moderno com suporte a:
  - WebAssembly
  - localStorage
  - Fullscreen API
  - File API

## Limitações

- Não inclui ROMs (o usuário deve fornecer)
- Dependência de CDN externa para o emulador
- Armazenamento limitado ao espaço do navegador
- Performance depende do dispositivo

## Segurança

Nenhum dado é enviado para servidores. Todos os arquivos e saves permanecem localmente no navegador do usuário.

## Licença

Este projeto utiliza o EmulatorJS, que possui sua própria licença. Verifique o repositório oficial para mais detalhes.
