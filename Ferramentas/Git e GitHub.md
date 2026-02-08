GIT = [Git](https://git-scm.com/) é um software de controle de versão de código aberto e gratuito. Ele permite que vários desenvolvedores trabalhem em um mesmo projeto ao mesmo tempo, sem que as alterações entrem em conflito. Também é usado nesse aplicativo para backup.

# 📌 Guia de Backup do Obsidian no GitHub

Este documento contém todos os passos necessários para configurar o backup do Obsidian no GitHub utilizando o Git.

---

## 🔹 1. Acessar a Pasta do Obsidian

O primeiro passo é abrir o terminal (Git Bash, Prompt de Comando ou Terminal) e navegar até a pasta onde está sua vault do Obsidian.

### **Comando:**

```bash
cd "C:\Users\SeuUsuario\Documents\ObsidianVault"
```

🔹 **O que faz?** Esse comando muda o diretório atual para a pasta do Obsidian.

**Exemplo (Windows):** `cd "C:\Users\aleilima\Documents\Estudos"`

**Exemplo (Mac/Linux):** `cd /home/SeuNome/ObsidianVault`

---

## 🔹 2. Inicializar o Repositório Git

Caso o repositório ainda não tenha sido inicializado, rode:

```bash
git init
```

🔹 **O que faz?** Cria um repositório Git dentro da pasta do Obsidian, permitindo rastrear as mudanças dos arquivos.

---

## 🔹 3. Criar um Repositório no GitHub

1. Acesse [GitHub](https://github.com/) e faça login.
    
2. Clique em **"New Repository"**.
    
3. Escolha um nome para o repositório (ex: `Obsidian-Backup`).
    
4. Marque **"Private"** se quiser que o repositório seja privado.
    
5. Clique em **"Create Repository"**.
    
6. O GitHub mostrará um link como:
    

```bash
https://github.com/SeuUsuario/Obsidian-Backup.git
```

Agora conectamos esse repositório remoto ao Git.

---

## 🔹 4. Conectar o Repositório Local ao GitHub

Execute este comando para adicionar o repositório remoto:

```bash
git remote add origin https://github.com/SeuUsuario/Obsidian-Backup.git
```

🔹 **O que faz?** Informa ao Git onde enviar os arquivos, conectando o repositório local ao remoto no GitHub.

Para verificar se o repositório foi adicionado corretamente:

```bash
git remote -v
```

🔹 **O que faz?** Lista os repositórios remotos configurados no Git.

Se aparecer algo como:

```bash
origin  https://github.com/SeuUsuario/Obsidian-Backup.git (fetch)
origin  https://github.com/SeuUsuario/Obsidian-Backup.git (push)
```

Então está tudo certo! 🚀

---

## 🔹 5. Criar a Branch `main` (se necessário)

Se o Git reclamar que não encontra a branch `main`, execute:

```bash
git branch -M main
```

🔹 **O que faz?** Renomeia a branch atual para `main`, garantindo que estamos na branch correta.

---

## 🔹 6. Adicionar Arquivos e Fazer o Primeiro Backup

Agora adicionamos todos os arquivos do Obsidian ao Git:

```bash
git add .
```

🔹 **O que faz?** Adiciona todos os arquivos modificados e novos ao estágio do Git para serem confirmados no próximo commit.

Criamos o primeiro commit:

```bash
git commit -m "Primeiro commit"
```

🔹 **O que faz?** Cria um snapshot das mudanças, armazenando-as localmente no histórico do Git.

E fazemos o envio para o GitHub:

```bash
git push -u origin main
```

🔹 **O que faz?** Envia os commits locais para o repositório remoto no GitHub.

---

## 🔹 7. Resolver Problemas de Push

Se aparecer o erro `error: src refspec main does not match any`, tente novamente os passos abaixo:

```bash
git branch -M main
git add .
git commit -m "Primeiro commit"
git push -u origin main
```

🔹 **O que faz?**

- `git branch -M main`: Renomeia a branch atual para `main`.
    
- `git add .`: Adiciona os arquivos ao estágio.
    
- `git commit -m "Primeiro commit"`: Cria um commit inicial.
    
- `git push -u origin main`: Envia as alterações para o GitHub.
    

Se o erro for `failed to push some refs`, tente primeiro fazer um pull antes do push:

```bash
git pull origin main --rebase
git push origin main
```

🔹 **O que faz?**

- `git pull origin main --rebase`: Puxa as mudanças do GitHub antes de enviar novas alterações.
    
- `git push origin main`: Envia os commits locais para o GitHub.
    

Se o erro persistir, force o push (⚠️ pode sobrescrever arquivos no GitHub):

```bash
git push -f origin main
```

🔹 **O que faz?** Força o envio dos arquivos, sobrescrevendo mudanças conflitantes no repositório remoto.

---

## 🔹 8. Como Atualizar o Backup Futuramente

Depois que o repositório já estiver configurado, basta rodar estes comandos sempre que quiser atualizar o backup:

```bash
git add .
git commit -m "Atualização das anotações"
git push
```

🔹 **O que faz?**

- `git add .`: Adiciona novos arquivos e alterações ao Git.
    
- `git commit -m "..."`: Cria um snapshot das mudanças.
    
- `git push`: Envia as mudanças para o GitHub.
    

---

## 🔹 9. Automação com Obsidian Git (Opcional)

Se quiser que o backup seja feito automaticamente, instale o plugin **Obsidian Git**:

1. No Obsidian, vá em **Configurações > Community Plugins**.
    
2. Habilite os plugins da comunidade e procure por **Obsidian Git**.
    
3. Instale e configure a frequência dos commits.
    

---

## 🔹 10. Baixar o Backup do GitHub em Outra Máquina

### **1. Clonar o Repositório**

```bash
git clone https://github.com/SeuUsuario/Obsidian-Backup.git
```

🔹 **O que faz?** Baixa todos os arquivos do repositório remoto para a máquina local.

Se quiser especificar a pasta:

```bash
git clone https://github.com/SeuUsuario/Obsidian-Backup.git "C:\Users\SeuUsuario\Documents\ObsidianVault"
```

### **2. Acessar a Pasta do Repositório**

```bash
cd Obsidian-Backup
```

🔹 **O que faz?** Entra na pasta clonada.

### **3. Manter o Backup Atualizado**

```bash
git pull origin main
```

🔹 **O que faz?** Baixa alterações mais recentes do GitHub.

Se quiser evitar conflitos:

```bash
git pull origin main --rebase
```