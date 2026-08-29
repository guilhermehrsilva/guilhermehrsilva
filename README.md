<h1 align="center">
  <code>~/</code> guilherme risson<span>&#9608;</span>
</h1>

<p align="center">
  <strong>AI Engineer</strong> &middot; RAG e avaliação &middot; sistemas de ML em produção &middot; contratos de dados
</p>

<p align="center">
  <img src="https://img.shields.io/badge/AI_Engineering-06152E?style=flat-square&labelColor=06152E&color=06152E" alt="AI Engineering" />
  <img src="https://img.shields.io/badge/RAG_&_Evaluation-123F8F?style=flat-square&labelColor=123F8F&color=123F8F" alt="RAG and Evaluation" />
</p>

---

```bash
~/ whoami
```

Construo **os sistemas em volta do modelo** — recuperação, avaliação, serving e os contratos de dados que impedem o sistema de apodrecer em silêncio. O modelo raramente é a parte difícil.

O fio condutor do que está aqui embaixo é medição: um harness que mostra que 80% das perguntas entregam norma revogada ao LLM; um validador que ranqueia defeitos de dados pelo quanto eles movem a decisão; um solver em produção com auditoria por rodada. Sistemas que dizem quando estão errados.

Finalizando pós-graduação em Ciência de Dados e cursando formação em AI Software Engineering.

📍 Maringá, Paraná &middot; Brasil

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
  <img src="https://img.shields.io/badge/BM25_Hybrid_Retrieval-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Evaluation_Harness-06152E?style=flat-square" />
</p>

**Backend &amp; Systems**
<p>
  <img src="https://img.shields.io/badge/FastAPI-123F8F?style=flat-square&logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/React-123F8F?style=flat-square&logo=react&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-123F8F?style=flat-square&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-123F8F?style=flat-square&logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/DuckDB-123F8F?style=flat-square&logo=duckdb&logoColor=white" />
  <img src="https://img.shields.io/badge/OR--Tools_(CP--SAT)-123F8F?style=flat-square" />
</p>

**Machine Learning**
<p>
  <img src="https://img.shields.io/badge/Scikit--Learn-06152E?style=flat-square&logo=scikitlearn&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/LightGBM-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/XGBoost-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/SHAP-06152E?style=flat-square" />
  <img src="https://img.shields.io/badge/Pandas-06152E?style=flat-square&logo=pandas&logoColor=FF6A45" />
  <img src="https://img.shields.io/badge/PyArrow-06152E?style=flat-square" />
</p>

---

```bash
~/ ls projetos/ --featured
```

### 🔍 [Regulatory RAG Eval](https://github.com/guilhermehrsilva/regulatory-rag-eval)
Harness de avaliação para RAG sobre 294 normativos do BACEN. **44,6% do corpus está revogado e a recuperação entrega norma morta ao modelo em 80% das perguntas** — e nenhuma métrica de similaridade acusa isso. Recuperação híbrida BM25 + densa, métricas e versionamento de corpus, medidos sem depender de LLM.
`sentence-transformers` · `rank-bm25` · `Gemini` · `pytest`

### 🧩 [Teacher Allocation Optimizer](https://github.com/guilhermehrsilva/teacher-allocation-optimizer)
Sistema full-stack de otimização com CP-SAT: validação de entrada, dois solvers isolados, auditoria por rodada e dashboard React. Suíte de testes, SBOM e inventário de licenças de terceiros.
`OR-Tools` · `FastAPI` · `React 19` · `TypeScript`

### 🩺 [Silent Data Defects](https://github.com/guilhermehrsilva/silent-data-defects)
Validador que ranqueia defeitos **pelo quanto mudam a decisão**, não por prevalência — e emite o contrato executável que impede o defeito de voltar. 5M × 26 colunas em 5s sobre 261 MB.
`DuckDB` · `PyArrow` · `CLI empacotada`

### 🤖 [Data Insight AI](https://github.com/guilhermehrsilva/data-insight-ai)
BI self-service em que o Gemini explora o dataset, recomenda KPIs e responde perguntas de negócio em linguagem natural, com fallback quando a API cai.
`Gemini` · `Streamlit` · `Plotly`

### 💳 [Credit Risk Decision Engine](https://github.com/guilhermehrsilva/credit-risk-decision-engine)
Separa prever de decidir: modelo de PD mais uma camada econômica que escolhe o corte por lucro esperado. **+24% de resultado sobre o threshold 0,50 — mesmo modelo, mesma AUC.**
`LightGBM` · `SHAP` · `Streamlit`

### 🚨 [Fraud Triage Under Capacity](https://github.com/guilhermehrsilva/fraud-triage-under-capacity)
Auditoria do PaySim: **uma regra de duas linhas pega 97,70% das fraudes sem modelo nenhum.** Reconstrução sem os atalhos do simulador, com a decisão modelada como triagem sob capacidade finita.
`LightGBM` · `Streamlit`

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
