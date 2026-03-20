# 🛠️ Relatório de Processo (Process Log) — Luiz Fernando Mendes

Este documento detalha a jornada de desenvolvimento do **Lead Scorer Inteligente**, desde a concepção estratégica até o deploy final, documentando o uso de múltiplas IAs e a supervisão humana crítica.

---

## 1. Concepção e Mentoria Estratégica
O projeto não começou com código, mas com estratégia. Criei um **GEM personalizado no Gemini chamado "Luiz"** (uma homenagem ao meu pai). Este agente foi alimentado com conhecimentos de psicologia comportamental, marketing e vendas (Napoleon Hill, Kotler).
- **Ação:** Definição da base de conhecimento e diretrizes do sistema.
- **Evidência:** ![Configuração do GEM Luiz](./screenshots/01.jpeg)

## 2. Exploração e Prototipagem (Python + Qwen)
Após validar a estratégia com o "Luiz", utilizei a IA **Qwen** para gerar o código bruto em Python. 
- **Workflow:** Gere o código na Qwen -> Validei a lógica com o Gemini -> Tentei rodar no **VS Code**.
- **Evidência de Geração:** ![Geração de código na Qwen](./screenshots/6.png)
- **Evidência de Análise:** ![Gemini analisando código da Qwen](./screenshots/12.png)

## 3. Desafios Técnicos e Intervenção Humana (Onde a IA Errou)

### A. Conflitos de Ambiente (Python 3.14)
Durante o build, enfrentei erros de dependência que a IA não previu. O sistema tinha múltiplas versões de Python.
- **Correção:** Forcei a instalação via `python -m pip` para garantir que o Streamlit funcionasse no ambiente correto.
- **Evidência:** ![Resolução de conflito Python](./screenshots/16.png)

### B. O Bug Crítico da Referência Temporal
O dataset é de 2017. A IA tentou calcular a "maturidade do lead" usando a data de hoje (2026), o que resultava em scores de "lead expirado" (zero) para todos os registros.
- **Correção:** Intervi para criar uma variável de `data_referencia` dinâmica baseada no último registro do CSV.
- **Evidência:** ![Identificação do erro de data](./screenshots/27.png)

### C. Ajustes de UI e Sintaxe
Erros de f-string e má formação de blocos de estilo CSS impediam a leitura correta dos dados no Dashboard.
- **Correção:** Debug manual no VS Code e unificação dos componentes visuais.
- **Evidência:** ![Ajuste de Design e Sintaxe](./screenshots/33.png)

## 4. Mudança de Rota Estratégica (Pivô para React)
Após 4 horas desenvolvendo em Python, percebi que o fluxo era lento e o visual não atingia o padrão G4. 
- **Decisão:** Abandonei o código Python e migrei para o **Google AI Studio** para reconstruir tudo em **React**.
- **Resultado:** Maior performance, design "SaaS Style" e melhor explicabilidade.
- **Evidência da Mudança:** ![Decisão de migrar para React](./screenshots/46.png)

## 5. Deploy e Infraestrutura Final
Utilizei o **Netlify** para colocar a aplicação em produção. Enfrentei erros no `requirements.txt` e caminhos de pasta, resolvidos através de ajustes no `index.html` e nas variáveis de ambiente do Netlify.
- **Evidência de Sucesso:** ![Deploy final no Netlify](./screenshots/52.png)

---

## 🧠 Conclusão: O Toque do AI Master
A IA foi o motor, mas o **julgamento humano** foi o piloto. A decisão de neutralizar o peso das "contas fantasmas" (leads sem Account) e a definição da **"Zona de Ouro" (30-120 dias)** foram conclusões analíticas próprias, garantindo que a ferramenta seja útil na prática comercial real.
