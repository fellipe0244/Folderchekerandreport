# Verificador de Caminhos Longos 🔍

O **Verificador de Caminhos Longos** é um aplicativo desktop nativo para Windows projetado para mapear diretórios e identificar arquivos ou pastas que excedem os limites padrão de caracteres do sistema operacional (limites de Alerta e Crítico). 

Este aplicativo foi desenvolvido combinando o poder de automação e varredura do **PowerShell** em segundo plano com uma interface gráfica moderna e exclusiva construída em **Electron (Node.js)**.

---

## 🚀 Funcionalidades

* **Varredura Segura:** O script apenas lê e analisa a estrutura de arquivos. **Não apaga, não move e não renomeia** nenhum dado do usuário.
* **Cálculo de Progresso Real (ETA):** Exibe uma barra de progresso visual em tempo real com base na estimativa de itens informada.
* **Logs Dinâmicos:** Mostra a contagem de itens verificados, alertas e críticos diretamente na tela durante a execução.
* **Exportação Inteligente:** Ao final do processo, o app pergunta ao usuário em qual pasta ele deseja salvar os relatórios.
* **Relatórios Completos:** Gera um arquivo `CSV` (otimizado para o Microsoft Excel) e um relatório visual em `HTML`.
* **Integração Nativa:** Permite abrir o relatório HTML diretamente no navegador padrão do sistema logo após a conclusão.

---

## 🛠️ Tecnologias Utilizadas

* **Frontend:** HTML5, CSS3 (Design responsivo integrado ao tema escuro estilo Windows Explorer)
* **Backend:** Node.js & Electron (v42.3.0)
* **Motor de Varredura:** PowerShell Core / Windows PowerShell (`Get-ChildItem` assíncrono via `child_process`)

---

## Downloads 

Disponibilizado a versão 1.0 com o executável e instalador para escolha do usuário.

A versão "VerificarCaminhosLongos" seja exe ou setup, funciona em SO mais recentes, pois tem o motor eléctron mais atualizado.

A versão "VerificarCaminhosLongos light" e "VerificarCaminhosLongos light Setup", são mais leves e funcionam em SO's mais antigos.

A versao .exe, é só executar, pode demorar para abrir carregando todos os componentes compilados.
A versao setup é de instalação.

https://github.com/fellipe0244/Folderchekerandreport/releases/tag/versions

## 💻 Como Rodar o Projeto em Desenvolvimento

Antes de começar, você vai precisar do [Node.js](https://nodejs.org/) instalado na sua máquina.

Developer by Fellipe Costa - ProjetoN1.SHOP
