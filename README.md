# Guia Git & GitHub — Apex Rocketry

Manual prático para os membros da **Apex Rocketry** baixarem os repositórios da organização, organizarem arquivos nas pastas corretas e enviarem alterações com segurança.

---

## 1. Configuração Inicial (Apenas na 1ª vez no PC)

Antes de começar, certifique-se de que o **Git** está instalado no seu computador. Em seguida, abra o terminal (Git Bash, PowerShell ou terminal do VS Code) e configure seu nome e e-mail (use o mesmo e-mail da sua conta no GitHub):

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@exemplo.com"
```

---

## 2. Baixar o Repositório pela Primeira Vez (`git clone`)

Você clona o repositório inteiro para o seu computador e trabalha dentro da pasta correspondente à sua tarefa ou subsistema.

1. Acesse o repositório desejado no GitHub (ex: `Eletronica`, `Aeroestruturas` ou `Propulsao`).
2. Clique no botão verde **`<> Code`** e copie a URL **HTTPS**.
3. No terminal, navegue até a pasta onde você salva seus projetos e execute:

```bash
git clone [https://github.com/Apex-Rocketry/NOME-DO-REPO.git](https://github.com/Apex-Rocketry/NOME-DO-REPO.git)
```

4. Entre na pasta do repositório:

```bash
cd NOME-DO-REPO
```

---

## 3. Fluxo Diário: Atualizar, Editar e Enviar Arquivos

Siga esta sequência toda vez que for trabalhar no projeto para evitar conflitos e manter a `main` limpa:

### Passo A: Atualizar a `main` local
Antes de criar uma nova *branch*, baixe as alterações mais recentes do GitHub:

```bash
git checkout main
git pull origin main
```

### Passo B: Criar uma *Branch* para a sua tarefa
**Nunca faça alterações ou `push` direto na `main`.** Crie uma *branch* específica para o que você vai fazer:

```bash
git checkout -b feat/nome-da-sua-tarefa
```

Exemplos de nomes de *branch*:
- `feat/estudos-joao`
- `feat/driver-sensor-bmp`
- `docs/pinout-modulo`
- `fix/ajuste-leitura-adc`

### Passo C: Salvar seus arquivos na pasta certa
Abra a pasta do repositório no seu computador e coloque seus arquivos no diretório adequado do projeto (como `docs/`, `estudos/`, `firmware/`, `ground-station/`, `hardware/` ou `test-bench/`, conforme a estrutura do repositório).

> **Atenção:** Se você estiver editando projetos de CAD ou PCB (como SolidWorks ou Altium), **feche o software** antes de commitar para evitar enviar arquivos temporários ou travados.

### Passo D: Adicionar, Commitar e Enviar (`add` → `commit` → `push`)
Dentro da pasta do repositório no terminal, execute:

1. Confira quais arquivos foram criados ou alterados:
   ```bash
   git status
   ```
2. Adicione os arquivos para o próximo *commit*:
   ```bash
   git add .
   ```
3. Registre o *commit* com uma mensagem clara:
   ```bash
   git commit -m "feat: adiciona arquivos de teste na pasta estudos"
   ```
4. Envie sua *branch* para o GitHub:
   ```bash
   git push -u origin feat/nome-da-sua-tarefa
   ```

---

## 4. Abrir o *Pull Request* (PR) no GitHub

Após concluir o `git push`:

1. Abra o repositório no navegador.
2. Clique em **Compare & pull request** na faixa exibida para a sua *branch*.
3. Descreva brevemente o que foi feito e em qual pasta os arquivos foram colocados, depois clique em **Create pull request**.
4. Marque ou avise o responsável/diretor do subsistema para revisar e fazer o *merge* na `main`.

---

## 5. Resumo Rápido de Comandos

| O que você quer fazer | Comando |
| :--- | :--- |
| Baixar um repositório novo | `git clone <URL-DO-REPO>` |
| Atualizar sua cópia local | `git checkout main` e `git pull origin main` |
| Criar uma *branch* nova | `git checkout -b feat/nome-da-tarefa` |
| Ver status dos arquivos | `git status` |
| Preparar todos os arquivos | `git add .` |
| Salvar o *commit* | `git commit -m "descricao da mudanca"` |
| Enviar a *branch* para o GitHub | `git push -u origin feat/nome-da-tarefa` |

---

## 6. Dúvidas ou Problemas Comuns

- **Erro de permissão / autenticação:** Verifique se você está logado na conta certa do GitHub no navegador/VS Code ou se aceitou o convite da organização **Apex-Rocketry**.
- **Conflito ao atualizar (`pull`):** Avise o líder do subsistema ou a diretoria de Eletrônica/Software antes de forçar qualquer comando.
- **Arquivos pesados ou temporários:** Verifique se o `.gitignore` do repositório já está cobrindo pastas de compilação, cache ou temporários antes de dar `git add .`.
