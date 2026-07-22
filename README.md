# 💻 Minhas Configurações de Terminal (Zsh & Oh My Zsh - Fedora)

Este repositório contém as minhas configurações personalizadas do **Zsh** com **Oh My Zsh** otimizadas para o **Fedora Workstation**. Ele serve tanto para facilitar a configuração de uma nova máquina do zero quanto para compartilhar com quem deseja ter um terminal produtivo, rápido e inteligente.

---

## 🚀 O que há de novo? (Fedora Edition)
A configuração anterior era baseada no Ubuntu e foi atualizada para focar no ecossistema do **Fedora**.
* **Plugins modernos:** Adicionado o autocomplete em tempo real.
* **Caminhos de desenvolvimento integrados:** Configurações prontas para **Flutter** e **Android SDK** (incluindo emulador e platform-tools).
* **Organização limpa:** Plugins externos gerenciados como submodules do Git.

---

## ⚙️ Pré-requisitos no Fedora

Antes de aplicar as configurações, você precisará ter o Zsh e o git instalados no seu sistema.

```bash
# 1. Instalar o Zsh e o Git
sudo dnf install zsh git -y

# 2. Definir o Zsh como shell padrão do seu usuário
chsh -s $(which zsh)
```
*(Nota: Pode ser necessário reiniciar a sessão/computador para aplicar a alteração do shell padrão).*

### Instalar o Oh My Zsh
O Oh My Zsh é o framework que gerencia nossa configuração. Instale-o com o comando abaixo:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

## 🔌 Plugins Inclusos e Ativos

Os plugins abaixo estão integrados a esta configuração. Eles aceleram a navegação e digitação no terminal:

1. **`git`**: Atalhos e aliases nativos para comandos do Git.
2. **`zsh-autosuggestions`**: Sugere comandos baseado no seu histórico de uso conforme você digita (estilo terminal Fish).
3. **`zsh-syntax-highlighting`**: Adiciona realce de sintaxe em tempo real aos comandos digitados (verde para comandos válidos, vermelho para inválidos).
4. **`zsh-autocomplete`**: Oferece autocompletar em tempo real conforme você digita, mostrando um menu interativo com opções de arquivos, comandos e históricos.

---

## 📥 Como Instalar e Aplicar

Siga o passo a passo abaixo para clonar e aplicar a configuração no seu terminal do zero.

### 1. Clonar o repositório recursivamente
Como os plugins estão configurados como submódulos do Git, você deve clonar o repositório trazendo estes arquivos:

```bash
# Clonar trazendo todos os submódulos de plugins
git clone --recursive https://github.com/takiguchii/zsh-config.git
cd zsh-config
```

> [!TIP]
> Se você já clonou de forma simples (sem `--recursive`), execute o comando abaixo para puxar os plugins:
> ```bash
> git submodule update --init --recursive
> ```

### 2. Fazer backup da configuração atual (Recomendado)
Se você já possui um arquivo `.zshrc` no seu sistema, faça um backup de segurança:
```bash
[ -f ~/.zshrc ] && cp ~/.zshrc ~/.zshrc.backup
```

### 3. Copiar os arquivos de configuração
Copie o arquivo `.zshrc` e a pasta `custom` (que contém os plugins e temas adicionais) para a sua pasta Home (`~`):

```bash
# Copiar o arquivo de configuração principal
cp .zshrc ~/

# Copiar a pasta customizada mantendo a estrutura
cp -r custom/* ~/.oh-my-zsh/custom/
```

### 4. Recarregar o Terminal
Para aplicar as alterações imediatamente sem fechar o terminal, execute:
```bash
source ~/.zshrc
```

---

## 🛠️ Detalhes da Configuração de Desenvolvimento

O `.zshrc` exportado está configurado de forma genérica e limpa com os seguintes caminhos utilitários de desenvolvimento:

### 📱 Android SDK & Emulador
Configurado automaticamente apontando para o diretório padrão no Linux:
* `ANDROID_HOME` definido como `$HOME/Android/Sdk`.
* Adicionado ao PATH:
  * O emulador de Android.
  * As ferramentas de plataforma (`platform-tools`, como `adb`).
  * Ferramentas de linha de comando mais recentes (`cmdline-tools`).

### 🐦 Flutter
Adiciona a pasta binária do Flutter ao PATH caso esteja instalada na pasta padrão:
* `$HOME/flutter/bin`

---

## 🔒 Cuidados com Arquivos Sensíveis

> [!CAUTION]
> **Nunca comite chaves de API, senhas ou tokens!**
> Se você for atualizar ou modificar este repositório com suas próprias alterações locais, tome os seguintes cuidados:
> 
> * Verifique se o seu `.zshrc` pessoal não contém tokens de API (ex: `GITHUB_TOKEN`, chaves OpenAI, etc.).
> * Se precisar exportar variáveis sensíveis localmente no seu terminal, prefira colocá-las em um arquivo separado que não seja rastreado pelo Git, por exemplo `~/.zsh_local` (adicionado ao seu `.gitignore` local) e dê source dele no seu `.zshrc` com:
>   ```bash
>   [ -f ~/.zsh_local ] && source ~/.zsh_local
>   ```

---

## 🔄 Como Exportar e Atualizar as Configurações

Caso você altere suas configurações locais no Fedora e queira salvá-las de volta neste repositório para manter o backup atualizado:

1. Acesse a pasta do repositório:
   ```bash
   cd ~/Documentos/github/zsh-config
   ```
2. Copie os arquivos da sua máquina para o repositório local:
   ```bash
   # Copia o .zshrc atualizado
   cp ~/.zshrc .zshrc
   
   # Opcional: Copia arquivos específicos da pasta custom
   cp -r ~/.oh-my-zsh/custom/* custom/
   ```
3. Remova trechos temporários ou sensíveis que tenham sido adicionados localmente antes de commitar.
4. Crie uma branch de alterações, realize o commit local e faça o push.

---

## 📄 Licença

Este projeto está sob a licença **MIT**. Veja o arquivo [LICENSE](file:///home/takiguchi/Documentos/github/zsh-config/LICENSE) para mais detalhes.
