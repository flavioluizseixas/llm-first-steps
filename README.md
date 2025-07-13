# 🧠 Chatbot com TinyLlama em Português

Este repositório apresenta quatro práticas de implementação de chatbots com modelos de linguagem, utilizando o modelo [TinyLlama 1.1B Chat](https://huggingface.co/TinyLlama/TinyLlama-1.1B-Chat-v1.0). As práticas estão organizadas por grau de complexidade crescente, desde uma execução simples em terminal até uma aplicação RAG (Retrieval-Augmented Generation) baseada em PDF com interface Gradio.

---

## 🟢 1. Execução Interativa em Terminal

**🔹 Enunciado:**  
Implemente um chatbot simples em terminal que responde perguntas em português, utilizando exemplos explícitos no prompt.

**🧩 Implementação:**  
O código carrega o modelo `TinyLlama-1.1B-Chat` da Hugging Face, define um prompt com instruções e exemplos, recebe uma pergunta via `input()` e gera uma resposta com `transformers`.

**🚀 Resultados Esperados:**
- Executado em ambiente local com suporte CUDA ou CPU.
- Geração de respostas coerentes em português com base em poucos-shots no prompt.

---

## 🟡 2. Chatbot com Gradio (Sem Memória)

**🔹 Enunciado:**  
Desenvolva uma interface web interativa com Gradio para o chatbot, permitindo que o usuário insira perguntas e receba respostas imediatamente, sem manter o histórico da conversa.

**🧩 Implementação:**  
A função `responder()` gera um prompt estático com exemplos fixos e insere a pergunta do usuário. A interface foi construída com `gr.Interface()` contendo um `Textbox` de entrada e saída.

**🚀 Resultados Esperados:**
- Interface visual simples e responsiva.
- Modelo responde de forma independente a cada pergunta, sem lembrar conversas anteriores.

---

## 🟠 3. Chatbot com Memória de Conversa (Histórico)

**🔹 Enunciado:**  
Crie um chatbot com histórico de interação, permitindo manter o contexto das conversas anteriores entre usuário e assistente.

**🧩 Implementação:**  
O prompt é construído dinamicamente com o histórico de pares (usuário, resposta). A interface foi construída com `gr.Blocks()` e inclui botão de limpar, `gr.Chatbot()` e controle de estado com `gr.State`.

**🚀 Resultados Esperados:**
- Mantém contexto conversacional entre perguntas.
- Interface simula uma conversa contínua com o assistente.

---

## 🔴 4. Chatbot com RAG a partir de PDF (Perguntas Baseadas em Contexto)

**🔹 Enunciado:**  
Implemente um sistema de RAG (Retrieval-Augmented Generation) com suporte a upload de PDF. O chatbot deve responder perguntas com base no conteúdo extraído do documento.

**🧩 Implementação:**  
1. Extrai texto do PDF usando `PyMuPDF`.
2. Divide o texto em chunks e gera embeddings com `SentenceTransformer`.
3. Usa `FAISS` para indexar os chunks e recuperar o mais relevante à pergunta.
4. Gera resposta contextualizada com base no chunk recuperado.
5. Interface Gradio com `gr.File`, `gr.Chatbot`, histórico e controle de estado.

**🚀 Resultados Esperados:**
- Upload e indexação de PDF textual.
- Perguntas respondidas com base no conteúdo do arquivo.
- Sistema robusto para construção de assistentes contextuais.

---

## 🧰 Requisitos

```bash
pip install torch transformers gradio sentence-transformers faiss-cpu pymupdf
