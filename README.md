# 🧠 Chatbots em Português com Qwen 2.5

Este repositório apresenta quatro práticas de implementação de chatbots com modelos de linguagem, utilizando o modelo [Qwen 2.5 3B Instruct](https://huggingface.co/Qwen/Qwen2.5-3B-Instruct). As práticas estão organizadas por grau de complexidade crescente, desde uma execução simples em terminal até uma aplicação RAG (Retrieval-Augmented Generation) baseada em PDF com interface Gradio.

---

## 🟢 1. Execução Interativa em Terminal

**🔹 Enunciado:**  
Implemente um chatbot simples em terminal que responde perguntas em português, utilizando exemplos explícitos no prompt.

**🧩 Implementação:**  
O notebook organiza o fluxo em etapas pequenas: configuração, carregamento do modelo, montagem das mensagens e geração da resposta.

**🚀 Resultados Esperados:**
- Executado em ambiente local ou Colab com GPU.
- Geração de respostas em português com um modelo pequeno, mas mais forte que o TinyLlama para uso geral.

---

## 🟡 2. Chatbot com Gradio (Sem Memória)

**🔹 Enunciado:**  
Desenvolva uma interface web interativa com Gradio para o chatbot, permitindo que o usuário insira perguntas e receba respostas imediatamente, sem manter o histórico da conversa.

**🧩 Implementação:**  
A função `responder()` encapsula a inferência do modelo e a interface foi construída com `gr.Interface()` contendo um `Textbox` de entrada e saída.

**🚀 Resultados Esperados:**
- Interface visual simples e responsiva.
- Cada pergunta é respondida de forma independente.

---

## 🟠 3. Chatbot com Memória de Conversa (Histórico)

**🔹 Enunciado:**  
Crie um chatbot com histórico de interação, permitindo manter o contexto das conversas anteriores entre usuário e assistente.

**🧩 Implementação:**  
As mensagens são construídas dinamicamente com o histórico de pares (usuário, resposta). A interface usa `gr.Blocks()`, `gr.Chatbot()` e `gr.State()` para deixar explícita a separação entre lógica e estado.

**🚀 Resultados Esperados:**
- Mantém contexto conversacional entre perguntas.
- Interface simula uma conversa contínua com o assistente.

---

## 🔴 4. Chatbot com RAG a partir de PDF (Perguntas Baseadas em Contexto)

**🔹 Enunciado:**  
Implemente um sistema de RAG (Retrieval-Augmented Generation) com suporte a upload de PDF. O chatbot deve responder perguntas com base no conteúdo extraído do documento.

**🧩 Implementação:**  
1. Extrai texto do PDF usando `PyMuPDF`.
2. Divide o texto em chunks.
3. Gera embeddings multilíngues com `SentenceTransformer`.
4. Usa `FAISS` para indexar os chunks e recuperar os trechos mais relevantes.
5. Gera resposta contextualizada com base no contexto recuperado.
6. Disponibiliza uma interface Gradio com upload, histórico e botão de limpar.

**🚀 Resultados Esperados:**
- Upload e indexação de PDF textual.
- Perguntas respondidas com base no conteúdo do arquivo.
- Sistema de RAG mais consistente para documentos em português.

---

## 🧰 Requisitos

```bash
pip install torch transformers accelerate gradio sentence-transformers faiss-cpu pymupdf
```
