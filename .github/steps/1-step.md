## Passo 1: Olá Copilot

Bem-vindo ao seu exercício **"Primeiros Passos com GitHub Copilot"**! :robot:

Neste exercício, você utilizará diferentes recursos do GitHub Copilot para trabalhar em um site que permite aos alunos da Escola Secundária Mergington se inscreverem em atividades extracurriculares. 🎻 ⚽️ ♟️

<img width="600" alt="screenshot of Mergington High School WebApp" src="../images/mergington-high-school-webapp.png" />

### 📖 Teoria: Conhecendo o GitHub Copilot

<img width="150" align="right" alt="copilot logo" src="../images/copilot-logo.png" />

GitHub Copilot é um assistente de codificação com IA que ajuda você a escrever código mais rápido e com menos esforço, permitindo que você dedique mais energia à resolução de problemas e colaboração.

GitHub Copilot foi comprovadamente aumentar a produtividade do desenvolvedor e acelerar o ritmo do desenvolvimento de software. Para mais informações, consulte [Pesquisa: quantificando o impacto do GitHub Copilot na produtividade e felicidade do desenvolvedor no blog do GitHub.](https://github.blog/news-insights/research/research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/)

Enquanto trabalha em seu IDE, você interagirá com o GitHub Copilot principalmente das seguintes maneiras:

| Modo de Interação          | 📝 Descrição                                                                                                                 | 🎯 Melhor para                                                                                                     |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| **⚡ Sugestões em linha** | Sugestões de código com IA que aparecem conforme você digita, oferecendo completações conscientes do contexto de uma única linha a funções inteiras. | Conclusão da linha atual, às vezes um bloco de código inteiro                                             |
| **💭 Chat em linha**        | Chat interativo limitado ao seu arquivo atual ou seleção. Faça perguntas sobre blocos de código específicos.                           | Explicações de código, depuração de funções específicas, melhorias direcionadas                                          |
| **💬 Modo de Pergunta**           | Otimizado para responder perguntas sobre sua base de código, programação e conceitos gerais de tecnologia.                                | Entender como o código funciona, brainstorming de ideias, fazer perguntas                                             |
| **🤖 Modo Agência**         | Modo padrão recomendado para a maioria das tarefas de codificação: edições autônomas, uso de ferramentas e execução até a conclusão da tarefa.         | Tarefas diárias de codificação, desde correções delimitadas a trabalho de implementação em múltiplos arquivos                                   |
| **🧭 Agente de Plano**         | Otimizado para rascunhar um plano e fazer perguntas esclarecedoras antes de qualquer alteração de código.                                | Quando você quer um plano revisado primeiro, depois delegar para implementação                                            |

As you work, you'll find GitHub Copilot can help out in several places across the `github.com` website and in your favorite coding environments such as VS Code, Jet Brains, and Xcode!

Por enquanto, vamos praticar com VS Code em um ambiente de desenvolvimento pré-configurado conhecido como [GitHub Codespace](https://github.com/features/codespaces).

> [!TIP]
> Você pode aprender mais sobre recursos atuais e futuros na documentação [Recursos do GitHub Copilot](https://docs.github.com/en/copilot/about-github-copilot/github-copilot-features).

### :keyboard: Atividade: Obter uma introdução do projeto do Copilot Chat

Vamos iniciar nosso ambiente de desenvolvimento, usar o copilot para aprender um pouco sobre o projeto e depois testá-lo.

1. Use o botão abaixo para abrir a página **Criar Codespace** em uma nova aba. Use a configuração padrão.

   [![Abrir no GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

1. Confirme se o campo **Repositório** é sua cópia do exercício, não o original, e clique no botão verde **Criar Codespace**.
   - ✅ Sua cópia: `/{{full_repo_name}}`
   - ❌ Original: `/skills/getting-started-with-github-copilot`

1. Aguarde um momento para o Visual Studio Code carregar em seu navegador.

1. Na barra lateral esquerda, clique na aba de extensões e verifique se as extensões `GitHub Copilot` e `Python` estão instaladas e habilitadas.

   <img width="350" alt="extensão copilot para VS Code" src="../images/copilot-extension-vscode.png" />

   <img width="350" alt="extensão python para VS Code" src="../images/python-extension-vscode.png" />

1. Na parte superior do VS Code, localize e clique no **ícone Toggle Chat** para abrir um painel lateral de Copilot Chat.

   <img width="150" alt="image" src="../images/toggle-chat-icon.png" />

   > 🪧 **Nota:** Se esta for sua primeira vez usando o GitHub Copilot, você precisará aceitar os termos de uso para continuar.

1. Certifique-se de estar em **Modo de Pergunta** para nossa primeira interação

   <img width="350" alt="captura de tela mostrando seleção de Modo de Pergunta no Copilot Chat" src="../images/ask-mode-selection.png" />

1. Digite o prompt abaixo para pedir ao Copilot para apresentar o projeto.

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > @workspace Please briefly explain the structure of this project.
   > What should I do to run it?
   > ```

   > 🪧 **Nota:** Não é necessário seguir as instruções recomendadas do Copilot. Já preparamos o ambiente para você.

   <details>
   <summary>O que é @workspace?</summary>

   Ótima pergunta! Este é um [participante de chat](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-participants) especializado que explorará o repositório do projeto e tentará incluir contexto relevante adicional.

   </details>

1. Agora que sabemos um pouco mais sobre o projeto, vamos realmente tentar executá-lo! Na barra lateral esquerda, selecione a aba `Executar e Depurar` e depois pressione o ícone **Iniciar Depuração**.

   <img width="300" alt="image" src="../images/run-and-debug-tab.png" />

1. Queremos ver nossa página da web rodando em um navegador, então vamos encontrar a url e a porta. Se não estiver visível, expanda o painel inferior e selecione a aba **Portas**.

1. Na lista, encontre a porta `8000` e o link relacionado. Passe o cursor sobre o link e selecione o ícone **Abrir no navegador**.

   ![image](../images/open-in-browser-icon.png)

### :keyboard: Atividade: Use Copilot para ajudar a lembrar um comando de terminal 🙋

Ótimo trabalho! Agora que estamos familiarizados com o aplicativo e sabemos que funciona, vamos pedir ao copilot ajuda para iniciar um branch para que possamos fazer algumas personalizações.

1. Na barra lateral esquerda do VS Code, selecione a aba **Terminal** e na parte direita clique no sinal de `+` para criar uma nova janela de terminal.

   > 🪧 **Nota:** Isso evitará parar a sessão de depuração existente que está hospedando nosso serviço de aplicativo web.

1. Dentro da nova janela de terminal, use o atalho de teclado `Ctrl + I` (Windows) ou `Cmd + I` (Mac) para abrir o **Copilot's Terminal Inline Chat**.

1. Vamos pedir ao Copilot ajuda para lembrar um comando que esquecemos: criar e publicar um branch Git.

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Hey copilot, how can I create and publish a new Git branch called "accelerate-with-copilot"?
   > ```

   > 💡 **Dica:** Se o Copilot não lhe der exatamente o que você quer, sempre pode continuar explicando o que precisa. Copilot se lembrará do histórico da conversa para respostas de acompanhamento.

1. Pressione o botão `Executar` para deixar o Copilot inserir o comando de terminal para nós. Não há necessidade de copiar e colar!

1. Após um momento, observe na barra de status inferior esquerda do VS Code para ver o branch ativo. Agora deve dizer `accelerate-with-copilot`. Se sim, você terminou este passo!

1. Agora que seu branch foi enviado para o GitHub, Mona já deve estar verificando seu trabalho. Dê um momento a ela e fique atento aos comentários. Você verá ela responder com informações de progresso e a próxima lição.

<details>
<summary>Com problemas? 🤷</summary><br/>

Se você não receber feedback, aqui estão algumas coisas a verificar:

- Certifique-se de que criou o branch com o nome exato `accelerate-with-copilot`. Sem prefixos ou sufixos.
- Certifique-se de que o branch foi de fato publicado no seu repositório.

</details>
