# 📌 Guia de Backup do Obsidian no GitHub

Este documento contém todos os passos necessários para configurar o backup do Obsidian no GitHub utilizando o Git.

---

## 🔹 1. Acessar a Pasta do Obsidian

O primeiro passo é abrir o terminal (Git Bash, Prompt de Comando ou Terminal) e navegar até a pasta onde está sua vault do Obsidian.

### **Comando:**

🔹 **O que faz?** Esse comando muda o diretório atual para a pasta do Obsidian.

**Exemplo (Windows):  C:\Users\aleilima\Documents\Estudos

**Exemplo (Mac/Linux) /home/SeuNome/ObsidianVault: 

---

## 🔹 2. Inicializar o Repositório Git

Caso o repositório ainda não tenha sido inicializado, rode:

🔹 **O que faz?** Cria um repositório Git dentro da pasta do Obsidian, permitindo rastrear as mudanças dos arquivos.

---

## 🔹 3. Criar um Repositório no GitHub

1. Acesse [GitHub](https://github.com/) e faça login.
2. Clique em **"New Repository"**.
3. Escolha um nome para o repositório (ex: `Obsidian-Backup`).
4. Marque **"Private"** se quiser que o repositório seja privado.
5. Clique em **"Create Repository"**.
6. O GitHub mostrará um link como:

Agora conectamos esse repositório remoto ao Git.

---

## 🔹 4. Conectar o Repositório Local ao GitHub

Execute este comando para adicionar o repositório remoto:

🔹 **O que faz?** Informa ao Git onde enviar os arquivos, conectando o repositório local ao remoto no GitHub.

Para verificar se o repositório foi adicionado corretamente:

🔹 **O que faz?** Lista os repositórios remotos configurados no Git.

Se aparecer algo como:

Então está tudo certo! 🚀

---

## 🔹 5. Criar a Branch `main` (se necessário)

Se o Git reclamar que não encontra a branch `main`, execute:

🔹 **O que faz?** Renomeia a branch atual para `main`, garantindo que estamos na branch correta.

---

## 🔹 6. Adicionar Arquivos e Fazer o Primeiro Backup

Agora adicionamos todos os arquivos do Obsidian ao Git:

🔹 **O que faz?** Adiciona todos os arquivos modificados e novos ao estágio do Git para serem confirmados no próximo commit.

Criamos o primeiro commit:

🔹 **O que faz?** Cria um snapshot das mudanças, armazenando-as localmente no histórico do Git.

E fazemos o envio para o GitHub:

🔹 **O que faz?** Envia os commits locais para o repositório remoto no GitHub.

---

## 🔹 7. Resolver Problemas de Push

Se aparecer o erro `error: src refspec main does not match any`, tente novamente os passos abaixo:

🔹 **O que faz?**

- `git branch -M main`: Renomeia a branch atual para `main`.
- `git add .`: Adiciona os arquivos ao estágio.
- `git commit -m "Primeiro commit"`: Cria um commit inicial.
- `git push -u origin main`: Envia as alterações para o GitHub.

Se o erro for `failed to push some refs`, tente primeiro fazer um pull antes do push:

🔹 **O que faz?**

- `git pull origin main --rebase`: Puxa as mudanças do GitHub antes de enviar novas alterações.
- `git push origin main`: Envia os commits locais para o GitHub.

Se o erro persistir, force o push (⚠️ pode sobrescrever arquivos no GitHub):

🔹 **O que faz?** Força o envio dos arquivos, sobrescrevendo mudanças conflitantes no repositório remoto.

---

## 🔹 8. Como Atualizar o Backup Futuramente

Depois que o repositório já estiver configurado, basta rodar estes comandos sempre que quiser atualizar o backup:

🔹 **O que faz?**

- `git add .`: Adiciona novos arquivos e alterações ao Git.
- `git commit -m "Atualização das anotações"`: Salva um novo snapshot das mudanças.
- `git push`: Envia as mudanças para o GitHub.

---

## 🔹 9. Automação com Obsidian Git (Opcional)

Se quiser que o backup seja feito automaticamente, instale o plugin **Obsidian Git**:

1. No Obsidian, vá em **Configurações > Community Plugins**.
2. Habilite os plugins da comunidade e procure por **Obsidian Git**.
3. Instale e configure a frequência dos commits.

---

Com isso, seu backup no GitHub estará sempre atualizado! 🚀😃