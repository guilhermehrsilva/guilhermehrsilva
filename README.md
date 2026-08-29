<h1 align="center">
  <code>~/</code> guilherme risson<span>&#9608;</span>
</h1>

<p align="center">
  <strong>AI Engineer</strong> &middot; recuperação &middot; avaliação &middot; serving &middot; contratos de dados
</p>

<p align="center">
  <img src="https://img.shields.io/badge/RAG_&_Retrieval-06152E?style=flat-square&labelColor=06152E&color=06152E" alt="RAG and Retrieval" />
  <img src="https://img.shields.io/badge/Evaluation_Harness-123F8F?style=flat-square&labelColor=123F8F&color=123F8F" alt="Evaluation Harness" />
  <img src="https://img.shields.io/badge/Production_ML-FF6A45?style=flat-square&labelColor=FF6A45&color=FF6A45" alt="Production ML" />
</p>

---

```bash
~/ whoami
```

Construo **os sistemas em volta do modelo**: recuperação, avaliação, serving e os contratos de dados que impedem tudo de apodrecer em silêncio. Montar um RAG é trabalho de uma tarde. Responder se dá para confiar nele é o trabalho.

Essa é a metade do problema que a maioria dos projetos pula, e é onde eu escolhi ficar.

Finalizando pós-graduação em Ciência de Dados e cursando formação em AI Software Engineering.

📍 Maringá, Paraná &middot; Brasil

---

```bash
~/ grep -r "competência" --evidência
```

| O que a área pede | Onde está, e o número |
|---|---|
| **Recuperação (RAG)** | Híbrida BM25 + E5 multilíngue, com fusão RRF sobre **posição** em vez de score: MRR **0,644** contra 0,361 do léxico puro, recall@1 de 0,133 para **0,533** |
| **Avaliação de sistemas de IA** | Conjunto dourado escrito à mão para evitar circularidade, harness de três blocos, **47 testes**. Contaminação de contexto medida: **80% das perguntas** entregam norma revogada ao modelo |
| **Chunking com propósito** | Segmentação por artigo porque é o que **torna a avaliação possível**. Sem a etiqueta do dispositivo no chunk, não há como cruzar citação com estado de vigência |
| **Serving e resiliência** | Limitador de taxa próprio, backoff exponencial para 503/500, medição de tokens, latência e custo por chamada. Rodada com erro é descartada, não reportada |
| **Saída estruturada e auditabilidade** | Citação obrigatória por afirmação, em campos separados. É o que transforma "conforme a Resolução X" em algo verificável por programa |
| **Contratos e qualidade de dados** | **71 checks** emitidos automaticamente de 26 colunas, com teste de duas proporções, correção de Bonferroni e piso de efeito prático contra alarme falso |
| **Monitoramento e drift** | PSI e CSI com o alarme **testado contra safra deteriorada**. O achado publicado foi que o PSI agregado **não** disparou |
| **Decisão sob restrição real** | Fila de revisão sob capacidade finita, ordenada por valor em risco: **77% do valor fraudado** barrado revisando **0,11%** do tráfego |
| **Engenharia de software** | `pytest` em quatro repositórios, CLI empacotada com `pyproject`, FastAPI + React 19 + TypeScript, SBOM CycloneDX e inventário de licenças de terceiros |
| **Performance de dados** | Três camadas de leitura sobre Parquet: **5M × 26 colunas em 4,8 s com 261 MB** de pico, com memória plana enquanto o dado cresce 50x |

---

```bash
~/ ls projetos/ --featured
```

### 🔍 [Regulatory RAG Eval](https://github.com/guilhermehrsilva/regulatory-rag-eval)

**Num corpus de 294 normativos do BACEN sobre Pix, 44,6% estão revogados, e a recuperação entrega norma morta ao modelo em 80% das perguntas.** Nenhuma métrica de similaridade acusa isso.

Não é um chatbot sobre regulação. É a medição de um. Recuperação híbrida com fusão RRF, resolução de dispositivos empilhados (o BACEN publica até **sete versões** do mesmo inciso coladas em sequência) e auditoria de vigência por citação. As duas camadas que sustentam o argumento **não usam LLM nenhum**.

`sentence-transformers` · `rank-bm25` · `RRF` · `Gemini` · `47 testes`

### 🧩 [Teacher Allocation Optimizer](https://github.com/guilhermehrsilva/teacher-allocation-optimizer)

Sistema full-stack de otimização com CP-SAT em operação: validação de entrada, **dois solvers deliberadamente isolados** (a aba de cenários não consegue sobrescrever a rodada publicada), auditoria por rodada e dashboard React.

Suíte de testes, SBOM CycloneDX e inventário de licenças de terceiros. É a prova de que entrego sistema, não notebook.

`OR-Tools (CP-SAT)` · `FastAPI` · `React 19` · `TypeScript` · `SBOM`

### 🩺 [Silent Data Defects](https://github.com/guilhermehrsilva/silent-data-defects)

**Ranqueia defeitos pelo quanto mudam a decisão, não por prevalência**, e emite o contrato executável que impede o defeito de voltar. O defeito em 7º lugar por prevalência sobe para 3º por impacto. O 4º inverte exatamente zero decisões.

25x mais rápido e 24x mais econômico em memória que o `ydata-profiling`, com precisão de 100% e **zero falsos positivos em 100 colunas limpas**. A margem até o limiar é apertada, e está publicada junto, registrada como limite conhecido.

`DuckDB` · `PyArrow` · `CLI empacotada`

### 🤖 [Data Insight AI](https://github.com/guilhermehrsilva/data-insight-ai)

BI self-service em que o Gemini explora o dataset, recomenda KPIs, gera 30+ tipos de gráfico e responde perguntas de negócio em linguagem natural. Tem modo de fallback que mantém os gráficos de pé quando a API cai.

`Gemini` · `Streamlit` · `Plotly`

### 💳 [Credit Risk Decision Engine](https://github.com/guilhermehrsilva/credit-risk-decision-engine)

**Trocar o corte de 0,50 pelo break-even econômico rendeu +24,0% na carteira de teste, com o mesmo modelo e a mesma AUC.** O corte ótimo sai de duas constantes de negócio e não olha uma linha do dataset. Ainda assim ganhou do ótimo procurado por varredura, que pegou ruído da amostra.

Reason codes por TreeSHAP exato, atributos protegidos fora das features e auditoria de paridade publicada **inclusive onde ela reprova** (0,767 no grupo até 25 anos, abaixo da regra dos 4/5).

`LightGBM` · `TreeSHAP` · `PSI/CSI` · `16 testes`

### 🚨 [Fraud Triage Under Capacity](https://github.com/guilhermehrsilva/fraud-triage-under-capacity)

**Uma regra de duas linhas, sem modelo nenhum, pega 97,70% das fraudes do PaySim.** Todo AUC de 0,99 publicado sobre esse dataset está reproduzindo essa regra com mais passos.

Audita o benchmark e reconstrói sem os atalhos: a PR-AUC honesta cai de 1,000 para 0,406 enquanto a ROC mal se move. A decisão vira triagem sob capacidade finita, onde ordenar por valor em risco pega **menos** fraudes e salva mais dinheiro.

`LightGBM` · `métricas de evento raro` · `18 testes`

---

```bash
~/ cat principios.txt
```

O que se repete nos quatro projetos acima não é o stack. É o hábito de publicar o número que incomoda:

- A geração do RAG **não tem métrica publicada**, porque a cota gratuita corrompeu a bateria. Métrica calculada sobre resposta que nunca chegou parece resultado, e é pior que métrica nenhuma.
- O contrato de validação **reprovava a base que o gerou**. O bug virou invariante: `emit` agora se recusa a gravar contrato que não passa na própria referência.
- O alarme de drift **não disparou** quando a aprovação caiu 7 pontos. Está publicado assim, com a conclusão de que PSI agregado sobre o escore é pouco sensível.
- A hipótese da conta laranja que acumula vítimas **não se confirmou**. O sinal real apontava para o lado oposto.

Sistema que não sabe dizer quando está errado não está pronto, e é essa camada que eu construo.

---

```bash
~/ cat skills.txt
```

**AI &amp; LLM**
<p>
  <img src="https://img.shields.io/badge/Python-06152E?style=flat-square&logo=python&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/RAG-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Gemini-06152E?style=flat-square&logo=googlegemini&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/Sentence--Transformers-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/BM25_+_RRF-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Structured_Output-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Eval_Harness-06152E?style=flat-square" />
</p>

**Backend &amp; Systems**
<p>
  <img src="https://img.shields.io/badge/FastAPI-123F8F?style=flat-square&logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/React_19-123F8F?style=flat-square&logo=react&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-123F8F?style=flat-square&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-123F8F?style=flat-square&logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/DuckDB-123F8F?style=flat-square&logo=duckdb&logoColor=white" />
  <img src="https://img.shields.io/badge/PyArrow-123F8F?style=flat-square" />
  <img src="https://img.shields.io/badge/OR--Tools_(CP--SAT)-123F8F?style=flat-square" />
</p>

**Machine Learning**
<p>
  <img src="https://img.shields.io/badge/LightGBM-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Scikit--Learn-06152E?style=flat-square&logo=scikitlearn&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/XGBoost-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/SHAP-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Pandas-06152E?style=flat-square&logo=pandas&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/pytest-06152E?style=flat-square&logo=pytest&logoColor=FF6A45" />
</p>

---

```bash
~/ contact --open
```

<p>
  <a href="https://www.linkedin.com/in/guilhermerisson/">
    <img src="https://img.shields.io/badge/LinkedIn-guilhermerisson-123F8F?style=flat-square&logo=linkedin&logoColor=white" />
  </a>
  <a href="mailto:guilherme.risson@outlook.com">
    <img src="https://img.shields.io/badge/Email-guilherme.risson@outlook.com-FF6A45?style=flat-square&logo=maildotru&logoColor=white" />
  </a>
</p>

<sub><code>~/</code> obrigado pela visita &middot; <em>Maringá, PR</em></sub>
