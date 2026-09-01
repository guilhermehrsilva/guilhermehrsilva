<h1 align="center">
  <code>~/</code> guilherme risson<span>&#9608;</span>
</h1>

<p align="center">
  <strong>AI Engineer</strong> &middot; dados &middot; backend &middot; negócio &middot; LLM no produto
</p>

<p align="center">
  <img src="https://img.shields.io/badge/RAG_&_Retrieval-06152E?style=flat-square&labelColor=06152E&color=06152E" alt="RAG and Retrieval" />
  <img src="https://img.shields.io/badge/Evaluation_Harness-123F8F?style=flat-square&labelColor=123F8F&color=123F8F" alt="Evaluation Harness" />
  <img src="https://img.shields.io/badge/Production_ML-FF6A45?style=flat-square&labelColor=FF6A45&color=FF6A45" alt="Production ML" />
</p>

<p align="center">
  <a href="https://guilhermehrsilva.github.io"><strong>guilhermehrsilva.github.io</strong></a>
</p>

<p align="center">
  <sub>Aberto a vagas de <strong>AI Engineer</strong> &middot; remoto ou Maringá/PR &middot; <a href="https://www.linkedin.com/in/guilhermerisson/">falar comigo no LinkedIn</a></sub>
</p>

---

```bash
~/ whoami
```

AI Engineer é quem junta quatro coisas: entende de **dado**, entende de **backend**, entende do **negócio**, e usa isso para colocar **LLM dentro do produto** de forma eficiente. Modelo é a parte fácil. O que decide se o sistema serve para alguma coisa é o que existe em volta dele.

Abaixo está a evidência de cada um dos quatro, com número. Depois, os projetos.

Finalizando pós-graduação em Ciência de Dados (UniCesumar) e cursando a Formação AI Software Engineer 4.0 (Data Science Academy).

📍 Maringá, Paraná &middot; Brasil

---

```bash
~/ cat pilares/negocio.md
```

**A decisão que muda, não a métrica que sobe.** É a diferença entre um modelo que funciona e um sistema que vale dinheiro.

- **+24% de resultado na carteira de teste com o mesmo modelo e a mesma AUC.** Trocar o corte de 0,50 pelo break-even econômico, que sai de duas constantes de negócio e não olha uma linha do dataset. O corte analítico ganhou do ótimo procurado por varredura, que pegou ruído da amostra.
- **77% do valor fraudado barrado revisando 0,11% do tráfego.** A mesa de análise revisa um número fixo de alertas por dia, então a pergunta não é qual o corte, é quais transações entram na fila. Ordenar por valor em risco pega menos fraudes e salva mais dinheiro, e um painel de recall registraria isso como piora.
- **Erro abaixo de 2% na estimativa da base de alunos**, 499 mil previstos contra 509 mil realizados, sustentando decisão de planejamento acadêmico na Vitru Educação.
- **Auditoria de paridade publicada inclusive onde ela reprova**, com o grupo até 25 anos em 0,767, abaixo da regra dos 4/5. Atributos protegidos deliberadamente fora das features.

```bash
~/ cat pilares/dados.md
```

**O dado que alimenta o sistema, e o contrato que impede ele de apodrecer.**

- **5M de linhas por 26 colunas em 4,8 s com 261 MB de pico**, memória plana enquanto o dado cresce 50x. Três camadas de leitura sobre Parquet com DuckDB e PyArrow.
- **71 checks emitidos automaticamente** de 26 colunas, com teste de duas proporções, correção de Bonferroni e piso de efeito prático contra alarme falso.
- **Defeitos ranqueados por impacto na decisão, não por prevalência.** O defeito em 7º por prevalência sobe para 3º por impacto; o 4º inverte exatamente zero decisões.
- **Integração e rastreabilidade de múltiplos sistemas corporativos** em SQL Server e Python, no dia a dia da Vitru Educação.

```bash
~/ cat pilares/backend.md
```

**O sistema que serve, com teste, contrato de interface e resiliência.**

- **FastAPI + React 19 + TypeScript** em sistema de otimização em operação, com dois solvers isolados por design: a aba de cenários não consegue sobrescrever a rodada publicada.
- **`pytest` em cinco repositórios**, CLI empacotada com `pyproject`, SBOM CycloneDX e inventário de licenças de terceiros.
- **Limitador de taxa próprio, backoff exponencial para 503 e 500**, com medição de tokens, latência e custo por chamada. Rodada com erro é descartada, não reportada.
- **Docker** e pipeline reprodutível de um clone limpo, sem artefato binário versionado.

```bash
~/ cat pilares/llm_no_produto.md
```

**LLM aplicado, e medido, que é a metade que a maioria dos projetos pula.**

- **Recuperação híbrida BM25 + E5 multilíngue com fusão RRF sobre posição**, elevando o MRR de 0,361 do léxico puro para 0,644 e o recall@1 de 0,133 para 0,533.
- **Contaminação de contexto medida em 80% das perguntas**, num corpus onde 44,6% dos normativos estão revogados. Nenhuma métrica de similaridade acusa isso.
- **Saída estruturada com citação obrigatória por afirmação**, em campos separados, que é o que torna a auditoria de vigência verificável por programa.
- **Chunking com propósito de avaliação**: segmentar por artigo é o que permite cruzar a citação da resposta com o estado de vigência do dispositivo.
- **Observabilidade da chamada**: tokens, latência e custo medidos por pergunta, com limitador de taxa próprio e backoff exponencial para 503 e 500. Erro transitório do provedor não vira número no relatório.
- **Guardrail contra alucinação**: o conjunto dourado inclui pergunta sem resposta no corpus, e a auditoria classifica citação inventada como `inexistente`, separada de norma revogada e de artigo revogado.
- **Gemini em produto self-service** que explora dataset, recomenda KPIs e responde em linguagem natural, com fallback que mantém os gráficos de pé quando a API cai.

---

```bash
~/ ls projetos/ --featured
```

### 🔍 [Regulatory RAG Eval](https://github.com/guilhermehrsilva/regulatory-rag-eval)

**Num corpus de 294 normativos do BACEN sobre Pix, 44,6% estão revogados, e a recuperação entrega norma morta ao modelo em 80% das perguntas.** Nenhuma métrica de similaridade acusa isso.

Não é um chatbot sobre regulação. É a medição de um. Recuperação híbrida com fusão RRF, resolução de dispositivos empilhados (o BACEN publica até **sete versões** do mesmo inciso coladas em sequência) e auditoria de vigência por citação. As duas camadas que sustentam o argumento **não usam LLM nenhum**.

`sentence-transformers` · `rank-bm25` · `RRF` · `Gemini` · `47 testes`

### 📄 [Procurement Triage Service](https://github.com/guilhermehrsilva/procurement-triage-service)

**O verificador não usa LLM: campo extraído só é aceito se o trecho citado existir literalmente no PDF e o valor parseado bater com ele.** É isso que transforma um resultado ruim em informação útil.

Triagem de editais do PNCP, com fila de leitura ordenada por valor esperado sob capacidade finita. No conjunto dourado de 7 editais rotulados à mão, prazo acertou **2 de 7**: o modelo confunde "abertura da sessão" com "prazo da proposta" mesmo com o prompt proibindo, e a citação correta é justamente o que prova que o erro é de julgamento, não de parsing. Depois da correção de prompt, a resposta errada com confiança virou abstenção com justificativa.

300 editais ingeridos, 96,7% com texto extraível sem OCR, orçamento de custo e timeout aplicado no código, US$ 0,028 por edital e p50 de 12,1 s. **Ciclo vermelho→verde demonstrado de verdade**: uma regressão foi reintroduzida de propósito, o portão de CI pegou, o PR seguinte corrigiu.

`FastAPI` · `Docker` · `Gemini` · `GitHub Actions` · `61 testes`

### 🩺 [Silent Data Defects](https://github.com/guilhermehrsilva/silent-data-defects)

**Ranqueia defeitos pelo quanto mudam a decisão, não por prevalência**, e emite o contrato executável que impede o defeito de voltar. O defeito em 7º lugar por prevalência sobe para 3º por impacto. O 4º inverte exatamente zero decisões.

25x mais rápido e 24x mais econômico em memória que o `ydata-profiling`, com precisão de 100% e **zero falsos positivos em 100 colunas limpas**. A margem até o limiar é apertada, e está publicada junto, registrada como limite conhecido.

`DuckDB` · `PyArrow` · `CLI empacotada`

### 🧩 [Teacher Allocation Optimizer](https://github.com/guilhermehrsilva/teacher-allocation-optimizer)

Sistema full-stack de otimização com CP-SAT em operação: validação de entrada, **dois solvers deliberadamente isolados** (a aba de cenários não consegue sobrescrever a rodada publicada), auditoria por rodada e dashboard React.

Suíte de testes, SBOM CycloneDX e inventário de licenças de terceiros. É a prova de que entrego sistema, não notebook.

`OR-Tools (CP-SAT)` · `FastAPI` · `React 19` · `TypeScript` · `SBOM`

### 💳 [Credit Risk Decision Engine](https://github.com/guilhermehrsilva/credit-risk-decision-engine)

**Trocar o corte de 0,50 pelo break-even econômico rendeu +24,0% na carteira de teste, com o mesmo modelo e a mesma AUC.** O corte ótimo sai de duas constantes de negócio e não olha uma linha do dataset. Ainda assim ganhou do ótimo procurado por varredura, que pegou ruído da amostra.

Reason codes por TreeSHAP exato, atributos protegidos fora das features e auditoria de paridade publicada **inclusive onde ela reprova** (0,767 no grupo até 25 anos, abaixo da regra dos 4/5).

`LightGBM` · `TreeSHAP` · `PSI/CSI` · `16 testes`

### 🚨 [Fraud Triage Under Capacity](https://github.com/guilhermehrsilva/fraud-triage-under-capacity)

**Uma regra de duas linhas, sem modelo nenhum, pega 97,70% das fraudes do PaySim.** Todo AUC de 0,99 publicado sobre esse dataset está reproduzindo essa regra com mais passos.

Audita o benchmark e reconstrói sem os atalhos: a PR-AUC honesta cai de 1,000 para 0,406 enquanto a ROC mal se move. A decisão vira triagem sob capacidade finita, onde ordenar por valor em risco pega **menos** fraudes e salva mais dinheiro.

`LightGBM` · `métricas de evento raro` · `18 testes`

### 🤖 [Data Insight AI](https://github.com/guilhermehrsilva/data-insight-ai)

BI self-service em que o Gemini explora o dataset, recomenda KPIs, gera 30+ tipos de gráfico e responde perguntas de negócio em linguagem natural. Tem modo de fallback que mantém os gráficos de pé quando a API cai.

`Gemini` · `Streamlit` · `Plotly`

---

```bash
~/ cat principios.txt
```

O que se repete nos projetos acima não é o stack. É o hábito de publicar o número que incomoda:

- A geração do RAG **não tem métrica publicada**, porque a cota gratuita corrompeu a bateria. Métrica calculada sobre resposta que nunca chegou parece resultado, e é pior que métrica nenhuma.
- O contrato de validação **reprovava a base que o gerou**. O bug virou invariante: `emit` agora se recusa a gravar contrato que não passa na própria referência.
- O alarme de drift **não disparou** quando a aprovação caiu 7 pontos. Está publicado assim, com a conclusão de que PSI agregado sobre o escore é pouco sensível.
- A hipótese da conta laranja que acumula vítimas **não se confirmou**. O sinal real apontava para o lado oposto.

Sistema que não sabe dizer quando está errado não está pronto, e é essa camada que eu construo.

---

```bash
~/ cat skills.txt
```

**LLM no produto**
<p>
  <img src="https://img.shields.io/badge/Python-06152E?style=flat-square&logo=python&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/RAG-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Gemini-06152E?style=flat-square&logo=googlegemini&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/Sentence--Transformers-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/BM25_+_RRF-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Embeddings-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Prompt_Engineering-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Structured_Output-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Guardrails-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/LLM_Observability-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Eval_Harness-06152E?style=flat-square" />
</p>

**Backend**
<p>
  <img src="https://img.shields.io/badge/FastAPI-123F8F?style=flat-square&logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/React_19-123F8F?style=flat-square&logo=react&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-123F8F?style=flat-square&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-123F8F?style=flat-square&logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/pytest-123F8F?style=flat-square&logo=pytest&logoColor=white" />
  <img src="https://img.shields.io/badge/Git-123F8F?style=flat-square&logo=git&logoColor=white" />
  <img src="https://img.shields.io/badge/REST_API-123F8F?style=flat-square" />
  <img src="https://img.shields.io/badge/OR--Tools_(CP--SAT)-123F8F?style=flat-square" />
</p>

**Dados**
<p>
  <img src="https://img.shields.io/badge/SQL_Server-06152E?style=flat-square&logo=microsoftsqlserver&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/DuckDB-06152E?style=flat-square&logo=duckdb&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/PyArrow-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Pandas-06152E?style=flat-square&logo=pandas&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/Data_Contracts-06152E?style=flat-square" />
</p>

**Negócio e decisão**
<p>
  <img src="https://img.shields.io/badge/LightGBM-FF6A45?style=flat-square&labelColor=06152E&color=06152E" />
  <img src="https://img.shields.io/badge/TreeSHAP-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Custo_de_erro_assim%C3%A9trico-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Drift_(PSI%2FCSI)-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Power_BI-06152E?style=flat-square&logo=powerbi&logoColor=FF6A45" />
</p>

---

```bash
~/ contact --open
```

Busco vagas de **AI Engineer**, com preferência por time que leva LLM para produção e se importa com o que acontece depois do deploy. Se é o seu caso, o código e as métricas dos projetos acima estão todos abertos aqui, inclusive os números ruins.

<p>
  <a href="https://www.linkedin.com/in/guilhermerisson/">
    <img src="https://img.shields.io/badge/LinkedIn-guilhermerisson-123F8F?style=flat-square&logo=linkedin&logoColor=white" />
  </a>
  <a href="mailto:guilherme.risson@outlook.com">
    <img src="https://img.shields.io/badge/Email-guilherme.risson@outlook.com-FF6A45?style=flat-square&logo=maildotru&logoColor=white" />
  </a>
</p>

<sub><code>~/</code> obrigado pela visita &middot; <em>Maringá, PR</em></sub>
