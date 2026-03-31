## Passo 4: Planeje Sua Implementação com o Agente de Planejamento 🧭

No último passo, o Modo Agência nos ajudou a se mover rápido e entregar nova funcionalidade. 🚀

Agora vamos desacelerar por uma rodada e trabalhar como arquitetos: definir uma abordagem forte de teste primeiro, depois delegar para implementação. Isso nos dá melhor clareza, menos surpresas e resultados mais limpos. 🧪

### 📖 Teoria: O que é Copilot Plan Agent?

Copilot [Plan Agent](https://code.visualstudio.com/docs/copilot/agents/planning) o ajuda a projetar uma solução antes de qualquer código ser alterado.

Em vez de pular direto para editações, ele pesquisa sua solicitação, faz perguntas esclarecedoras e rascunha um plano de implementação que você pode refinar.

#### Plan Agent (de uma olhada)

| Aspecto | 🧭 Plan Agent |
| --- | --- |
| Propósito | Cria um plano de implementação estruturado antes que a codificação comece. |
| Coleta de contexto | Usa pesquisa somente leitura para entender os requisitos e restrições. |
| Estilo de colaboração | Faz perguntas esclarecedoras, depois atualiza o plano usando suas respostas. |
| Iteração | Suporta múltiplas passagens de refinamento antes da implementação. |
| Segurança | Não edita arquivos até que você aprove o plano e delegue para **Modo Agência**. |
| Delegacão | Botão **Iniciar implementação** delega o plano aprovado para **Modo Agência** para codificação. |

> [!TIP]
> Você pode começar a partir de uma solicitação de alto nível e depois adicionar restrições e detalhes em prompts de acompanhamento.

### ⌨️ Atividade: Planejar e implementar testes de backend

Seu backend ainda tem cobertura zero de testes. Use **Plan Agent** para criar um plano, responda perguntas e depois inicie a implementação.

1. Abra o painel **Copilot Chat** e mude para **Plan Agent**.

   <img width="350" alt="image" src="../images/plan-mode-dropdown.png" />


1. Vamos começar com um prompt amplo e o Copilot nos ajudará a preencher os detalhes:

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > I want to add backend FastAPI tests in a separate tests directory.
   > ```

1. Aguarde o Copilot gerar seu primeiro plano. Se fizer alguma pergunta, responda da melhor forma que puder.

   > 🪧 **Nota:** Não se preocupe em acertá-lo perfeitamente, você sempre pode refinar o plano depois.

1. Você pode refinar o plano e fornecer detalhes adicionais em prompts de acompanhamento

   Aqui estão alguns exemplos:

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Let's use the AAA (Arrange-Act-Assert) testing pattern to structure our tests
   > ```

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Make sure we use `pytest` and add it to `requirements.txt` file
   > ```


1. Review the proposed plan and when you are happy with it, click **Start implementation** to hand off to **Agent Mode**.

   <img width="350" alt="image" src="../images/plan-mode-start-implementation.png" />

   Notice that clicking the button switched from **Plan** to **Agent Mode**. From this point on, Copilot can edit your codebase, just like before.

1. Watch Copilot implement the plan you just created. It may ask for permissions to run certain tools (e.g., run commands or create virtual environments). Approve these permissions so it can continue working.

1. Review the changes and make sure tests run successfully. If needed, continue guiding until implementation is complete.

   **🎯 Goal: Get all tests passing (green) before you move on. ✅**

   > 🪧 **Note:** Agent Mode may complete this in one pass, or it may need follow-up prompts from you.

1. **Commit** and **push** all your changes to the `accelerate-with-copilot` branch.

1. Wait for Mona to check your work and share the next step.

<details>
<summary>Having trouble? 🤷</summary><br/>

- If tests did not run, ask Copilot to run them for you.
- Make sure `pytest` is added in `requirements.txt` and a `tests/` directory exists.

</details>
