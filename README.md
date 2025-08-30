# Configurações do Zsh

Repositório com minhas configurações personalizadas do **Zsh**, incluindo plugins e temas, para facilitar reinstalações e migração entre computadores.

---

## 🚀 Instalação rápida

```bash
# Clonar o repositório
git clone https://github.com/takiguchii/zsh-config.git
cd zsh-config

# Fazer backup do .zshrc atual (se existir)
[ -f ~/.zshrc ] && mv ~/.zshrc ~/.zshrc.backup

# Copiar minhas configs
cp .zshrc ~/

# (Opcional) Copiar configuração do Powerlevel10k
[ -f .p10k.zsh ] && cp .p10k.zsh ~/

# (Opcional) Copiar pastas customizadas do Oh My Zsh
[ -d custom ] && cp -r custom/* ~/.oh-my-zsh/custom/
```

---

## 🔌 Plugins recomendados

Se estiver usando **Oh My Zsh**, instale também:

```bash
# Autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions   ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# Syntax Highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git   ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Depois, edite o `.zshrc` e adicione:

```zsh
plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
)
```

---

## 🎨 Tema (Powerlevel10k)

Se quiser usar o **Powerlevel10k**:

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git   ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k
```

E no seu `~/.zshrc`, altere a linha do tema:

```zsh
ZSH_THEME="powerlevel10k/powerlevel10k"
```

---

## 🔄 Atualizando a configuração

Para salvar uma nova versão das configs neste repositório:

```bash
# Entrar na pasta do repositório
cd ~/zsh-config

# Copiar suas novas configs
cp ~/.zshrc .zshrc
[ -f ~/.p10k.zsh ] && cp ~/.p10k.zsh .p10k.zsh
cp -r ~/.oh-my-zsh/custom/ custom/

# Commit e push
git add .
git commit -m "Atualiza minhas configs do Zsh"
git push origin main
```

---

## 📦 Sobre

Este repositório me ajuda a manter minhas configurações de Zsh organizadas e prontas para serem usadas em qualquer máquina.
