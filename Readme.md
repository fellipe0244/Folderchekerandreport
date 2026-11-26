# 🔍 Folder Checker and Report

### Verificador de Caminhos Longos — Local, Rede e Microsoft Cloud

O **Folder Checker and Report** é um aplicativo desktop para Windows desenvolvido para mapear diretórios, analisar estruturas de armazenamento e identificar arquivos ou pastas que excedem os limites de comprimento de caminho.

O projeto combina o poder de automação do **PowerShell**, a integração com a **Microsoft Graph API** e uma interface gráfica desenvolvida em **Electron (Node.js)**.

A partir da versão 2.0, o aplicativo passou a oferecer suporte à verificação diretamente no **Microsoft SharePoint e OneDrive**, sem a necessidade de mapear unidades de rede, sincronizar pastas ou baixar arquivos da nuvem.

---

## ☁️ Ambientes suportados

| Ambiente | Tecnologia | Versão |
|---|---|---|
| Diretórios locais | PowerShell | V1 e V2 |
| HDs e SSDs | PowerShell | V1 e V2 |
| Servidores de arquivos | PowerShell / SMB | V1 e V2 |
| Unidades de rede mapeadas | PowerShell | V1 e V2 |
| SharePoint Online | Microsoft Graph API | V2 |
| OneDrive corporativo | Microsoft Graph API | V2 |
| OneDrive pessoal | Microsoft Graph API | V2 |

---

## 🚀 Funcionalidades

- **Varredura segura:** analisa a estrutura de armazenamento sem apagar, mover, renomear ou modificar os arquivos.
- **Integração Microsoft Cloud:** conexão direta com SharePoint Online e OneDrive por meio da Microsoft Graph API.
- **Autenticação segura:** login realizado no navegador oficial da Microsoft, utilizando OAuth 2.0 com PKCE, sem armazenamento de senhas ou necessidade de Client Secret.
- **Navegação por diretórios:** seleção de pastas, bibliotecas de documentos e subpastas.
- **Varredura recursiva:** análise dos arquivos e subdiretórios da origem selecionada.
- **Barra de progresso:** acompanhamento visual da execução, com percentual calculado ou estimado de acordo com o ambiente.
- **Cronômetro:** acompanhamento do tempo decorrido durante a varredura e apresentação da duração final.
- **Contadores dinâmicos:** quantidade de itens verificados, alertas e ocorrências críticas.
- **Análise de armazenamento:** contabilização de arquivos, pastas e volume dos arquivos analisados.
- **Controle de cobertura:** identificação de erros de acesso e resultados parciais.
- **Exportação inteligente:** seleção do diretório de destino dos relatórios.
- **Relatórios interativos:** exportação em CSV e HTML navegável.
- **Tutorial integrado:** instruções ilustradas para configuração e autenticação no Microsoft Entra ID.

---

## 📊 Relatórios interativos

A versão 2.0 conta com um modelo de relatório HTML compartilhado entre os ambientes Local/Rede e Microsoft Cloud.

Os relatórios possuem:

- Dashboard com resumo da varredura.
- Quantidade de arquivos e pastas.
- Volume total dos arquivos analisados.
- Data, horário e duração do processamento.
- Classificação de alertas e críticos.
- Pesquisa instantânea por nome ou caminho.
- Filtros por status e tipo de item.
- Ordenação das ocorrências.
- Paginação dos resultados.
- Navegação em árvore de diretórios.
- Expansão e recolhimento de pastas.
- Identificação de pendências e falhas de acesso.
- Links diretos para os arquivos analisados na nuvem.

O relatório HTML pode ser aberto diretamente no navegador e consultado offline. Os links para arquivos na nuvem dependem de conexão e das permissões do usuário.

Também é disponibilizado um arquivo CSV compatível com o Microsoft Excel, permitindo análises complementares.

---

## 📏 Critérios de verificação

O aplicativo utiliza critérios distintos para cada ambiente, respeitando as particularidades dos sistemas de armazenamento.

| Classificação | Local / Rede | Microsoft Cloud |
|---|---:|---:|
| Normal | Até 260 caracteres | Abaixo do limite de alerta |
| Alerta | Acima de 260 caracteres | A partir de 350 caracteres |
| Crítico | Acima de 290 caracteres | Acima de 400 caracteres |

O limite de alerta para Microsoft Cloud pode ser personalizado pelo usuário.

Os critérios locais são parâmetros de diagnóstico utilizados pelo aplicativo. O suporte a caminhos longos no Windows pode variar de acordo com a configuração do sistema operacional e dos aplicativos utilizados.

A verificação na nuvem considera o comprimento do caminho decodificado, que não corresponde necessariamente ao caminho de uma pasta sincronizada no Windows.

---

## 🔐 Configuração Microsoft Cloud

Para utilizar a integração com SharePoint e OneDrive, é necessário registrar um aplicativo no [Microsoft Entra ID](https://entra.microsoft.com/).

### Configuração inicial

1. Acesse o portal Microsoft Entra ID.
2. Entre em **Registros de aplicativo**.
3. Crie um novo registro.
4. Defina o nome do aplicativo.
5. Selecione o tipo de conta compatível com o ambiente desejado.
6. Configure o redirecionamento como **Cliente público/nativo (móvel e desktop)**.
7. Utilize a URI de redirecionamento `http://localhost`.
8. Configure as permissões delegadas do Microsoft Graph.
9. Copie o ID do aplicativo (cliente) e o ID do diretório (locatário).
10. Preencha os respectivos campos no Folder Checker and Report.

### Permissões utilizadas

| API | Permissão delegada | Finalidade |
|---|---|---|
| Microsoft Graph | `Files.Read` | Leitura dos arquivos do OneDrive |
| Microsoft Graph | `Sites.Read.All` | Leitura dos sites e bibliotecas do SharePoint |
| Microsoft Graph | `offline_access` | Renovação da autenticação durante a sessão |

Não é necessário criar um Client Secret ou adicionar permissões da API específica do SharePoint.

Dependendo das políticas de segurança da organização, poderá ser necessário o consentimento de um administrador.

O aplicativo possui um **tutorial ilustrado integrado à interface**, com capturas reais do portal Microsoft Entra ID, facilitando todo o processo de configuração.

---

## 🛡️ Segurança e privacidade

O Folder Checker and Report foi desenvolvido para operar exclusivamente em modo de leitura.

- Não exclui arquivos.
- Não movimenta arquivos.
- Não renomeia diretórios.
- Não modifica documentos.
- Não baixa o conteúdo dos arquivos da nuvem.
- Não armazena senhas Microsoft.
- Não necessita de um servidor intermediário próprio.
- Utiliza permissões delegadas do usuário.
- Mantém os relatórios na máquina do usuário.
- Mantém os tokens de autenticação em memória durante a sessão.

A cobertura da varredura depende das permissões da conta autenticada. Itens não acessíveis ou ocultados pelo provedor podem não ser contabilizados.

---

## 🛠️ Tecnologias utilizadas

| Tecnologia | Aplicação |
|---|---|
| HTML5 | Estrutura da interface e dos relatórios |
| CSS3 | Identidade visual e responsividade |
| JavaScript | Eventos, interações e processamento |
| Node.js | Backend e integração dos motores |
| Electron | Aplicativo desktop Windows |
| PowerShell | Varredura de diretórios locais e de rede |
| Microsoft Graph API | Integração com SharePoint e OneDrive |
| OAuth 2.0 / PKCE | Autenticação Microsoft |
| Electron Builder | Compilação do executável e instalador |

---

## 📥 Downloads

Os executáveis e instaladores publicados estão disponíveis na seção de releases do GitHub.

**[Acessar downloads e versões disponíveis](https://github.com/fellipe0244/Folderchekerandreport/releases)**

### Versão 2.0 — Microsoft Cloud

Nova geração do aplicativo, desenvolvida para sistemas Windows modernos.

Inclui os motores de varredura Local/Rede e Microsoft Cloud, relatórios interativos, autenticação Microsoft e tutorial de configuração integrado.

### Versão 1.0 — Original

Versão destinada à verificação de diretórios locais, servidores e unidades de rede.

### Versão 1.0 Light

Edição legada desenvolvida com uma versão anterior do Electron, destinada a sistemas operacionais mais antigos.

Não possui integração com Microsoft Cloud e utiliza dependências antigas, sem as atualizações de segurança da edição moderna.

### Formatos de distribuição

| Formato | Descrição |
|---|---|
| Executável portátil (.exe) | Execução sem instalação |
| Setup (.exe) | Instalação convencional no Windows |
| Light | Edição legada da versão 1.0 |

A versão portátil pode apresentar um pequeno tempo de carregamento inicial devido à extração e inicialização dos componentes internos.

---



## 📈 Evolução do projeto

| Versão | Principais alterações |
|---|---|
| V1.0 | Varredura local e de rede, exportação CSV e HTML |
| V2.0.0 | Integração SharePoint e OneDrive |
| V2.0.1 | Revisão de segurança, organização e documentação do código |
| V2.0.2 | Relatório HTML interativo para Microsoft Cloud |
| V2.0.3 | Unificação dos relatórios Local/Rede e Cloud |
| V2.0.4 | Tutorial de configuração Microsoft integrado |
| V2.0.5 | Tutorial ilustrado com capturas reais do Microsoft Entra |
| V2.0.6 | Barra de progresso e cronômetro nos dois ambientes |
| V2.0.7 | Refinamento visual e organização dos relatórios |

---

## 🎯 Próximas evoluções

- [x] Verificação de diretórios locais.
- [x] Verificação de servidores e unidades de rede.
- [x] Integração com Microsoft SharePoint.
- [x] Integração com Microsoft OneDrive.
- [x] Relatórios HTML interativos.
- [x] Navegação em árvore de diretórios.
- [x] Tutorial Microsoft integrado.
- [x] Barra de progresso e cronômetro.
- [ ] Integração com Google Drive.
- [ ] Integração com outros provedores de armazenamento.
- [ ] Análise de compatibilidade para migração entre ambientes.
- [ ] Histórico e comparação de auditorias.
- [ ] Varredura incremental.

---

## 👨‍💻 Desenvolvimento

Projeto desenvolvido com o objetivo de facilitar atividades de infraestrutura, administração de ambientes corporativos, diagnóstico de armazenamento e planejamento de migrações.

**Developer by Fellipe Costa**

**ProjetoN1.SHOP**

[GitHub](https://github.com/fellipe0244) | [Website](https://www.projeton1.shop)

---

*Folder Checker and Report — Local, Network & Cloud Storage Audit.*
