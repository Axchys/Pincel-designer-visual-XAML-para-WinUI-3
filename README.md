# 🖌️ Pincel

**Designer visual de XAML para WinUI 3, com a interface do Blend for Visual Studio.**

O Pincel abre soluções e projetos WinUI 3 e deixa você montar as telas (`.xaml`) arrastando, desenhando e mexendo nas propriedades, ou escrevendo o XAML direto num editor de código com IntelliSense. Os dois lados ficam sincronizados o tempo todo.

Feito em **C# + WinUI 3** (Windows App SDK 2.5.1, .NET 8), com tema escuro no estilo do Visual Studio 2026. O editor de código é o **Monaco** (o mesmo do VS Code), rodando local dentro de um WebView2.

> Versão atual: **0.2.2** · Plataforma: **Windows 10 (1809+) / Windows 11** · Arquiteturas: **x64 e ARM64**

---

## Índice

- [Por que o Pincel](#por-que-o-pincel)
- [Recursos](#recursos)
- [Requisitos](#requisitos)
- [Como rodar](#como-rodar)
- [Abrindo projetos](#abrindo-projetos)
- [A interface](#a-interface)
- [Designer](#designer)
- [Editor de código](#editor-de-código)
- [Galeria de exemplos](#galeria-de-exemplos)
- [Atalhos](#atalhos)
- [Desempenho e robustez](#desempenho-e-robustez)
- [Privacidade e rede](#privacidade-e-rede)
- [Estrutura do repositório](#estrutura-do-repositório)
- [Testes](#testes)
- [Solução de problemas](#solução-de-problemas)
- [Licenças de terceiros](#licenças-de-terceiros)

---

## Por que o Pincel

Desenhar telas de WinUI 3 hoje exige abrir o Visual Studio inteiro. O Pincel é um app leve, só pro design: abre o seu projeto, mostra as telas renderizadas de verdade com os controles do WinUI, e salva direto nos seus arquivos `.xaml`. Compilar e rodar o projeto também funciona, usando o `dotnet` do seu computador.

## Recursos

- **Designer visual** com artboard, alças, mover, redimensionar e desenhar controles.
- **Editor XAML (Monaco)** com IntelliSense feito a partir dos tipos reais do WinUI.
- **Sincronização nos dois sentidos** entre o texto e o designer.
- **Estados visuais** com gravação: escolha um estado, mexa nas propriedades e vira `Setter` no `VisualState`.
- **Linha do tempo** de animações: crie um `Storyboard`, mova a agulha e vira quadro-chave.
- **Trilhos do Grid** para criar colunas e linhas clicando, com proporções em estrela como no Blend.
- **Recursos do `App.xaml`** do seu projeto entram no preview (estilos, cores, `ResourceDictionary` mesclados).
- **Gerenciador de Soluções**, painel de **Ativos**, **Lista de Erros** e **Saída**.
- **Git integrado**: branch, alterações, buscar, puxar e enviar.
- **Compilar e iniciar** o projeto direto do Pincel.
- **Galeria** com 278 exemplos de XAML prontos para inserir.
- Interface toda em **português do Brasil**.

## Requisitos

| Item | Versão |
| --- | --- |
| Sistema | Windows 10 1809 (build 17763) ou mais novo; Windows 11 recomendado |
| Visual Studio | 2022 ou 2026, com a carga de trabalho **Desenvolvimento de aplicativos do Windows / WinUI** |
| SDK do .NET | 8.0 ou mais novo |
| WebView2 Runtime | Já vem no Windows 11. Sem ele, o Pincel abre um editor de texto simples no lugar e avisa |
| Git | Opcional, só para o painel de Git |

## A interface

Segue o layout do Blend:

- **Barra de título:** logo, menus (*Arquivo, Editar, Exibir, Git, Projeto, Compilar, Depurar, Teste, Analisar, Ferramentas, Extensões, Janela, Ajuda*), caixa **Pesquisar (Ctrl+Q)** que acha qualquer comando ou arquivo da solução.
- **Barra de ferramentas:** novo item, Debug / Any CPU, **▶ Iniciar** (compila e roda), iniciar sem depurar, parar, abrir a pasta da solução.
- **Esquerda, em cima:** *Gerenciador de Soluções*, com abas **Ativos** e **Estados**. Tem busca e menu de contexto (adicionar Página, UserControl, Janela, Dicionário, Classe; renomear; excluir; compilar).
- **Esquerda, embaixo:** *Objetos e Linha do Tempo* (em arquivos C#, vira *Estrutura de Tópicos do Documento*).
- **Centro:** abas de documento, régua, trilha de navegação, artboard com moldura de janela, barra do designer (zoom, grade, ajustar à grade, fundo xadrez, linhas de ajuste, tema, tamanho) e abas **Design ⇅ XAML** com divisão horizontal ou vertical.
- **Direita:** *Propriedades* e *Alterações do Git*.
- **Embaixo:** *Lista de Erros* e *Saída*, e a barra de status com branch do Git e Ln/Car, SPC, CRLF, UTF-8.

## Designer

- Ferramentas: seleção, seleção direta, mão, zoom, pincel, caneta, retângulo, elipse, Border, Grid, StackPanel, TextBlock e Button.
- **Seleção múltipla** (Ctrl/Shift+clique ou retângulo), alinhar, igualar tamanho e mover em grupo.
- **Agrupar em Grid** (Ctrl+G) e desagrupar (Ctrl+Shift+G).
- **AdaptiveTrigger** reage ao tamanho do artboard, não ao da janela do Pincel.
- **Gravação de estado** com moldura vermelha "gravação ativada".
- **Linha do tempo:** arraste quadros-chave, toque, pare, vá pro começo ou pro fim.

## Editor de código

- Cores do VS escuro para XAML, C#, JSON, XML, Markdown e outras.
- **IntelliSense de XAML:** elementos, propriedades, eventos, valores de enum, cores, propriedades anexadas (`Grid.Row`), `{ThemeResource ...}`. Fecha a tag sozinho e coloca `""` depois do `=`.
- Erros de XML sublinhados na hora e também na Lista de Erros.
- Dobrar regiões, formatar documento, localizar/substituir em português.
- **Clicar no texto seleciona o elemento** no artboard, e **selecionar no artboard seleciona a tag** no texto. O designer só envia o trecho que mudou, então cursor e desfazer do editor não se perdem.
- Arquivos `.cs`: navegação em 3 listas (projeto, classe, membro) e estrutura de tópicos. **F7** alterna entre código e designer.

## Galeria de exemplos

O painel **Ativos › Galeria** traz 278 trechos de XAML organizados em 18 grupos (Coleções, Entrada básica, Menus e barras, Texto, Movimento, Navegação, Layout, Estilos e outros). Os exemplos vêm do [WinUI 3 Gallery](https://github.com/microsoft/WinUI-Gallery) (licença MIT).

## Atalhos

**Ferramentas**

| Tecla | Ferramenta |
| --- | --- |
| `V` | Seleção |
| `A` | Seleção direta |
| `H` | Mão |
| `Z` | Zoom |
| `M` | Retângulo |
| `L` | Elipse |
| `B` | Border |
| `G` | Grid |
| `K` | StackPanel |
| `T` | Texto |
| `U` | Botão |
| `P` | Caneta |

**Geral**

| Atalho | Ação |
| --- | --- |
| `Ctrl+N` | Nova página |
| `Ctrl+O` / `Ctrl+Shift+O` | Abrir arquivo / projeto ou solução |
| `Ctrl+S` / `Ctrl+Shift+S` | Salvar / salvar tudo |
| `Ctrl+F4` | Fechar documento |
| `Ctrl+Z` / `Ctrl+Y` | Desfazer / refazer |
| `Ctrl+X` `Ctrl+C` `Ctrl+V` | Recortar, copiar, colar |
| `Ctrl+D` | Duplicar |
| `Del` | Excluir |
| `Esc` | Seleciona o pai |
| `Ctrl+A` | Selecionar tudo |
| Setas | Movem 1 px (com `Shift`, 10 px) |
| `Ctrl+Shift+B` | Compilar |
| `F5` / `Ctrl+F5` / `Shift+F5` | Iniciar / iniciar sem depurar / parar |
| `Ctrl+Q` | Pesquisar |
| `F4` | Propriedades |
| `Ctrl+Alt+L` | Gerenciador de Soluções |
| `F7` | Código / designer |
| `Ctrl+Tab` | Próximo documento |
| `F1` | Lista completa de atalhos |

## Desempenho e robustez

- Preview agrupado: várias mudanças seguidas viram um carregamento só, e XAML igual não recarrega.
- Adornos atualizados só quando algo mexe.
- Raiz do projeto e recursos do `App.xaml` em cache (lidos de novo só quando o arquivo muda).
- Desfazer guarda só a diferença do texto (até 1000 passos, com limite de memória).
- Tipos do WinUI carregados em segundo plano na abertura.
- A seleção segue o elemento pela posição no texto, então editar o XAML não pula a seleção.
- Salvar preserva o fim de linha original (CRLF não vira LF).
- Se o processo do editor cair, ele reinicia e reabre os documentos sozinho.
- Erros vão para `%LOCALAPPDATA%\Pincel\pincel.log` e para a janela *Saída*.

## Privacidade e rede

O Pincel só usa a rede quando **você** manda: compilar/rodar (`dotnet build` pode restaurar pacotes do NuGet) e comandos de Git com remoto (buscar, puxar, enviar).

O editor, o IntelliSense e o preview são **100% locais**: as páginas do editor vêm da pasta `Assets/Editor` e qualquer outro endereço é bloqueado. O `dotnet` roda com telemetria desativada.

## Estrutura do repositório

```
Pincel/
├── Pincel.sln
├── src/
│   ├── Pincel.Core/            Lógica sem WinUI (testável): modelo de XAML, edição,
│   │                           diff de texto, desfazer, soluções, animação, Grid
│   └── Pincel/                 O app WinUI 3
│       ├── Shell/              Janelas de ferramenta e abas de documento
│       ├── Documents/          Visão de cada documento aberto
│       ├── Design/             Artboard, régua, propriedades e tipos do WinUI
│       ├── Editor/             Ponte com o Monaco e esquema do XAML
│       ├── Panels/             Soluções, Ativos, Estados, Objetos, Propriedades,
│       │                       Git, Lista de Erros, Saída
│       ├── Build/              Compilar (dotnet) e cliente de Git
│       ├── Infra/              Tema, configurações, ícones, log
│       └── Assets/             Monaco compilado, ponte JS, galeria.json, ícone
└── tests/
    └── Pincel.Core.Tests/      Testes do Core
```

## Testes

Os testes cobrem o `Pincel.Core` (a parte sem interface) e rodam em qualquer sistema com o .NET 8:

```bash
dotnet run --project tests/Pincel.Core.Tests
```

## Solução de problemas

- **Erro de compilação:** abra a **Lista de Erros** e copie tudo ao abrir uma issue.
- **Editor aparece como texto simples:** falta o WebView2 Runtime. Instale pelo site da Microsoft.
- **`dotnet` não encontrado ao compilar:** instale o SDK do .NET (ou o Visual Studio).
- **Algo deu errado e não sei o quê:** veja `%LOCALAPPDATA%\Pincel\pincel.log`.

## Licenças de terceiros

- **Monaco Editor 0.57.0** (MIT), Microsoft.
- **WinUI 3 Gallery** (MIT), Microsoft: origem dos exemplos da galeria.

Textos completos em [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).
