# 🤖 Configurando GitHub Copilot Agent no Linux Mint

## ❓ Por que o Copilot aparece riscado?

O ícone do Copilot aparece **riscado** na barra de status do VS Code quando a autenticação OAuth com o GitHub **não foi concluída pelo VS Code**.

> ⚠️ **Atenção**: Autenticar a chave SSH no GitHub **não** ativa o Copilot.  
> O Copilot exige autenticação via conta GitHub (OAuth/token), feita dentro do próprio VS Code ou via GitHub CLI (`gh`).

---

## ✅ Pré-requisitos

- Linux Mint atualizado
- VS Code instalado
- Extensão **GitHub Copilot** instalada no VS Code
- Conta GitHub com assinatura ativa do Copilot ([verificar em github.com/settings/copilot](https://github.com/settings/copilot))

---

## 📦 Passo 1: Instalar o GitHub CLI (`gh`)

O GitHub CLI permite autenticar sua conta GitHub no terminal e integra com o VS Code.

```bash
# Adicionar o repositório oficial do GitHub CLI
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg \
  | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null

echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] \
  https://cli.github.com/packages stable main" \
  | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null

sudo apt update && sudo apt install -y gh
```

Verificar instalação:

```bash
gh --version
```

---

## 🔑 Passo 2: Autenticar com o GitHub via CLI

Execute o comando abaixo e siga as instruções interativas:

```bash
gh auth login
```

Quando solicitado, selecione as seguintes opções:

```
? What account do you want to log into?  → GitHub.com
? What is your preferred protocol?        → HTTPS
? Authenticate Git with your GitHub credentials? → Yes
? How would you like to authenticate GitHub CLI? → Login with a web browser
```

- Copie o código de 8 dígitos exibido no terminal.
- Um navegador será aberto automaticamente (ou use o link exibido).
- Cole o código em [github.com/login/device](https://github.com/login/device).
- Autorize o acesso.

Verificar autenticação:

```bash
gh auth status
```

Resultado esperado:

```
✓ Logged in to github.com as SEU_USUARIO (oauth_token)
✓ Git operations for github.com configured to use https protocol.
```

---

## 🧩 Passo 3: Instalar as extensões do Copilot no VS Code

Abra o terminal e instale as extensões necessárias:

```bash
code --install-extension GitHub.copilot
code --install-extension GitHub.copilot-chat
```

Ou instale pelo marketplace do VS Code (`Ctrl+Shift+X`), buscando por:
- **GitHub Copilot**
- **GitHub Copilot Chat**

---

## 🔐 Passo 4: Autenticar o Copilot dentro do VS Code

1. Abra o VS Code.
2. Pressione `Ctrl+Shift+P` para abrir a paleta de comandos.
3. Digite: `GitHub: Sign in` e pressione Enter.
4. Siga o fluxo de autenticação no navegador.

> Se o VS Code não abrir o navegador automaticamente, clique em **"Allow"** na notificação que aparecer no canto inferior direito.

Após autenticar, o ícone do Copilot na barra de status deve ficar **ativo (sem risco)**.

---

## 🛠️ Solução de Problemas

### Problema: O navegador não abre automaticamente no Linux Mint

Instale o `xdg-utils` para que o terminal consiga abrir o navegador padrão:

```bash
sudo apt install -y xdg-utils
```

### Problema: Copilot continua riscado após autenticação

Verifique se sua conta tem assinatura ativa do Copilot:

```bash
gh api user | grep login
# Acesse: https://github.com/settings/copilot
```

Verifique o status de autenticação no VS Code:

```bash
# Pressione Ctrl+Shift+P e execute:
# "GitHub Copilot: Check Status"
```

Reinicie o VS Code completamente:

```bash
pkill code
code .
```

### Problema: Erro "Could not connect to GitHub Copilot"

Verifique sua conexão e autentique novamente:

```bash
gh auth logout
gh auth login
```

---

## 🔍 Diferença entre SSH e OAuth para o Copilot

| Autenticação | Uso                                 | Copilot?  |
|--------------|-------------------------------------|-----------|
| **SSH Key**  | Push/pull de repositórios via `git` | ❌ Não ativa o Copilot |
| **OAuth/Token** (`gh auth login`) | Autorização de apps GitHub (Copilot, CLI) | ✅ Necessário para o Copilot |

> Você pode (e deve) ter **ambas** configuradas: SSH para operações git, e OAuth para o Copilot.

---

## ✅ Verificação Final

Após completar todos os passos:

1. O ícone do Copilot na barra de status do VS Code deve estar **ativo** (sem risco).
2. Ao abrir um arquivo de código, o Copilot deve oferecer sugestões automáticas.
3. O chat do Copilot deve estar acessível via `Ctrl+Alt+I` ou no painel lateral.

```bash
# Confirmar autenticação ativa
gh auth status

# Confirmar extensões instaladas
code --list-extensions | grep -i copilot
```

---

## 📚 Referências

- [Documentação oficial do GitHub Copilot](https://docs.github.com/en/copilot)
- [GitHub CLI - Autenticação](https://cli.github.com/manual/gh_auth_login)
- [Extensão Copilot no VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)
