## Passo 2: Realizando Trabalho com Copilot

No passo anterior, o GitHub Copilot foi capaz de nos ajudar a integrar ao projeto. Isso por si só é uma grande economia de tempo, mas agora vamos fazer algum trabalho!

:bug: **HÁ UM BUG NO SITE** :bug:

Descobrimos que algo está errado no fluxo de inscrição.
Os alunos podem se registrar na mesma atividade **mais de uma vez**! Vamos ver até onde o Copilot pode nos levar na descoberta da causa e na modelagem de uma solução limpa.

Antes de nos aprofundarmos, uma rápida cartilha sobre como o Copilot funciona. 🧠‍🚀

### 📖 Teoria: Como Copilot Funciona

Em resumo, você pode pensar no Copilot como um colega de trabalho muito especializado. Para ser eficaz com ele, você precisa fornecer contexto (background) e direção clara (prompts). Além disso, pessoas diferentes são melhores em coisas diferentes por causa de suas experiências únicas (modelos).

- **Como fornecemos contexto?:** Em nosso ambiente de codificação, o Copilot considerará automaticamente código próximo e abas abertas. Se você estiver usando chat, também pode se referir explicitamente aos arquivos.

- **Que modelo devemos escolher?:** Para nosso exercício, não deve importar muito. Experimentar com diferentes modelos é parte da diversão! Essa é outra lição! 🤖

- **Como faço prompts?:** Ser explícito e claro ajuda o Copilot a fazer o melhor trabalho. Mas diferentemente de alguns sistemas tradicionais, você sempre pode esclarecer sua direção com prompts de acompanhamento.

> [!TIP]
> Existem várias outras maneiras de suplementar o conhecimento e os recursos do Copilot, como [participantes de chat](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-participants), [variáveis de chat](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-variables), [comandos slash](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#slash-commands-1), e [ferramentas MCP](https://code.visualstudio.com/docs/copilot/chat/mcp-servers).

### :keyboard: Atividade: Use Copilot para corrigir nosso bug de registro :bug:

1. Vamos pedir ao Copilot para sugerir de onde nosso bug pode estar vindo. Abra o painel **Copilot Chat** no **Modo de Pergunta** e faça o seguinte.

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > @workspace Students are able to register twice for an activity.
   > Where could this bug be coming from?
   > ```

1. Agora que sabemos que o problema está no arquivo `src/app.py` e no método `signup_for_activity`, vamos seguir a recomendação do Copilot e resolvê-lo (semi-manualmente). Começaremos com um comentário e deixaremos o Copilot terminar a correção.
   1. Abra o arquivo `src/app.py`.

      > 💡 **Dica:** Se o Copilot mencionou `src/app.py` no chat, você pode clicar no arquivo diretamente na visualização do chat para abri-lo.

   1. Perto do final do arquivo, encontre a função `signup_for_activity`.

   1. Encontre a linha de comentário que descreve a adição de um aluno. Acima disso é onde parece lógico fazer nossa verificação de registro.

   1. Digite o comentário abaixo e pressione Enter para ir para a próxima linha. Após um momento, o texto de sombra temporária aparecerá com uma sugestão do Copilot! Legal! :tada:

      Comentário:

      ```python
      # Validate student is not already signed up
      ```

      <img width="700" alt="Sugestão de texto de sombra do Copilot no editor" src="../images/shadow-text.gif" />

   1. Pressione `Tab` para aceitar a sugestão do Copilot e converter o texto de sombra em código.

   <details>
   <summary>Resultados do Exemplo</summary><br/>

   Copilot está crescendo todos os dias e pode não produzir sempre os mesmos resultados. Se você não estiver satisfeito com as sugestões, aqui está um exemplo de resultado de sugestão válido que produzimos durante a realização deste exercício. Você pode usá-lo para continuar adiante.

   ```python
   @app.post("/activities/{activity_name}/signup")
   def signup_for_activity(activity_name: str, email: str):
      """Sign up a student for an activity"""
      # Validate activity exists
      if activity_name not in activities:
         raise HTTPException(status_code=404, detail="Activity not found")

      # Get the activity
      activity = activities[activity_name]

      # Validate student is not already signed up
      if email in activity["participants"]:
        raise HTTPException(status_code=400, detail="Student is already signed up")

      # Add student
      activity["participants"].append(email)
      return {"message": f"Signed up {email} for {activity_name}"}
   ```

   </details>

### :keyboard: Atividade: Deixe Copilot Gerar Dados de Amostra 📑

Em novos desenvolvimentos de projetos, geralmente é útil ter alguns dados falsos realistas para testes. Copilot é excelente nesta tarefa, então vamos adicionar mais atividades de amostra e apresentar outra forma de interagir com Copilot usando **Chat em Linha**

**Chat em Linha** e o painel **Copilot Chat** são semelhantes, mas diferem em escopo: Copilot Chat lida com perguntas mais amplas, multi-arquivo ou exploratórias; Chat em Linha é mais rápido quando você quer ajuda direcionada na linha ou bloco exato na sua frente.

1. Perto do topo do arquivo `src/app.py` (cerca da linha 23), encontre a variável `activities`, onde as atividades extracurriculares de amostra são configuradas.

1. Destaque todo o dicionário `activities` clicando e arrastando seu mouse de cima para baixo do dicionário. Isso ajudará a fornecer contexto ao Copilot para nosso próximo prompt.

   <img width="700" alt="Dicionário de atividades destacado antes de abrir chat em linha" src="../images/activities-dict-highlighted.png" />


1. Abra o chat em linha do Copilot usando o comando de teclado `Ctrl + I` (Windows) ou `Cmd + I` (Mac).

   > 💡 **Dica:** Outra forma de abrir o chat em linha do Copilot é: `clique com botão direito` em qualquer uma das linhas selecionadas -> `Abrir Chat em Linha`.

1. Digite o seguinte texto de prompt e pressione Enter ou o botão **Enviar** à direita.

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Add 2 more sports related activities, 2 more artistic
   > activities, and 2 more intellectual activities.
   > ```

1. Após um momento, o Copilot começará a fazer alterações no código. As alterações serão estilizadas de forma diferente para facilitar a identificação de adições e remoções. Reserve um momento para inspecionar e verificar as alterações e pressione o botão **Manter**.

   <details>
   <summary>Resultados do Exemplo</summary><br/>

   Copilot está crescendo todos os dias e pode não produzir sempre os mesmos resultados. Se você não estiver satisfeito com as sugestões, aqui está um resultado de exemplo que produzimos durante a realização deste exercício. Você pode usá-lo para continuar, se tiver problemas.

   ```python
   # In-memory activity database
   activities = {
      "Chess Club": {
         "description": "Learn strategies and compete in chess tournaments",
         "schedule": "Fridays, 3:30 PM - 5:00 PM",
         "max_participants": 12,
         "participants": ["michael@mergington.edu", "daniel@mergington.edu"]
      },
      "Programming Class": {
         "description": "Learn programming fundamentals and build software projects",
         "schedule": "Tuesdays and Thursdays, 3:30 PM - 4:30 PM",
         "max_participants": 20,
         "participants": ["emma@mergington.edu", "sophia@mergington.edu"]
      },
      "Gym Class": {
         "description": "Physical education and sports activities",
         "schedule": "Mondays, Wednesdays, Fridays, 2:00 PM - 3:00 PM",
         "max_participants": 30,
         "participants": ["john@mergington.edu", "olivia@mergington.edu"]
      },
      "Basketball Team": {
         "description": "Competitive basketball training and games",
         "schedule": "Tuesdays and Thursdays, 4:00 PM - 6:00 PM",
         "max_participants": 15,
         "participants": []
      },
      "Swimming Club": {
         "description": "Swimming training and water sports",
         "schedule": "Mondays and Wednesdays, 3:30 PM - 5:00 PM",
         "max_participants": 20,
         "participants": []
      },
      "Art Studio": {
         "description": "Express creativity through painting and drawing",
         "schedule": "Wednesdays, 3:30 PM - 5:00 PM",
         "max_participants": 15,
         "participants": []
      },
      "Drama Club": {
         "description": "Theater arts and performance training",
         "schedule": "Tuesdays, 4:00 PM - 6:00 PM",
         "max_participants": 25,
         "participants": []
      },
      "Debate Team": {
         "description": "Learn public speaking and argumentation skills",
         "schedule": "Thursdays, 3:30 PM - 5:00 PM",
         "max_participants": 16,
         "participants": []
      },
      "Science Club": {
         "description": "Hands-on experiments and scientific exploration",
         "schedule": "Fridays, 3:30 PM - 5:00 PM",
         "max_participants": 20,
         "participants": []
      }
   }
   ```

   </details>

1. Agora você pode ir ao seu site e verificar se as novas atividades são visíveis.

### :keyboard: Atividade: Use Copilot para descrever nosso trabalho 🗨🏿

Ótimo trabalho corrigindo esse bug e expandindo as atividades de amostra! Agora vamos fazer nosso trabalho ser commitado e enviado para o GitHub, novamente com a ajuda do Copilot!

1. Na barra lateral esquerda, selecione a aba `Controle de Fonte`.

   > 💡 **Dica:** Abrir um arquivo da área de controle de fonte mostrará as diferenças do original em vez de simplesmente abri-lo.

1. Encontre o arquivo `app.py` e pressione o sinal de `+` para coletar suas alterações juntas na área de preparação.

   ![image](../images/staging-changes-icon.png)

1. Acima da lista de alterações preparadas, encontre a caixa de texto **Mensagem**, mas **não digite nada** por enquanto.
   - Normalmente, você escreveria uma breve descrição das alterações aqui, mas agora temos Copilot para ajudar!

1. À direita da caixa de texto **Mensagem**, encontre e clique no botão **Gerar Mensagem de Commit** (ícone de centelhas).

1. Pressione o botão **Commit** e o botão **Sincronizar Alterações** para enviar suas alterações para o GitHub.

1. Aguarde um momento para Mona verificar seu trabalho, fornecer feedback e compartilhar a próxima lição.

<details>
<summary>Com problemas? 🤷</summary><br/>

Se você não receber feedback, aqui estão algumas coisas a verificar:

- Certifique-se de ter feito push das alterações do arquivo `src/app.py` para o branch `accelerate-with-copilot`.

</details>
