# Comandos para hospedagem compartilhada

## Instalação do NVM/NODE/NPM

### Instalar NVM no seu usuário
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

### Ativar o NVM
```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```

### Instalar Node.js (junto vem o npm)
```bash
nvm install 22
```

