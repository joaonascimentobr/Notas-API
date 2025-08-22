# 🐧 Cola Rápida: PATH no Linux

## 🔹 O que é o PATH?
- Variável de ambiente que guarda **a lista de diretórios onde o sistema procura executáveis**.  
- Em vez de rodar `/usr/bin/ls`, basta digitar `ls`.

Ver o PATH atual:
```bash
echo $PATH
```

---

## 🔹 Como funciona a ordem
O sistema procura **na ordem dos diretórios listados**.  
O **primeiro executável encontrado** é o usado.

Exemplo:
```bash
type -a python
```
Saída:
```
/usr/bin/python
/home/joao/.local/bin/python
```
👉 `/usr/bin/python` será usado porque vem antes no PATH.

---

## 🔹 Adicionar diretórios ao PATH
### Apenas para a sessão atual:
```bash
export PATH=$PATH:/meu/diretorio
```

### Permanente (para bash):
Edite `~/.bashrc` e adicione:
```bash
export PATH=$PATH:/meu/diretorio
```

### Permanente (para zsh):
Edite `~/.zshrc`:
```bash
export PATH=$PATH:/meu/diretorio
```

Recarregar:
```bash
source ~/.bashrc
# ou
source ~/.zshrc
```

---

## 🔹 Alterar prioridade
Para dar prioridade ao diretório do usuário:
```bash
export PATH=$HOME/.local/bin:$PATH
```
👉 Agora tudo em `~/.local/bin` será procurado antes de `/usr/bin`.

---

## 🔹 Remover diretórios do PATH
### Temporário (sessão atual):
```bash
export PATH=$(echo $PATH | sed -e 's;:/usr/local/bin;;g')
```

### Permanente:
Edite `~/.bashrc` e **não inclua** o diretório indesejado.

---

## 🔹 Dicas práticas
- **Ver onde está um executável**:
  ```bash
  which comando
  ```
- **Listar todos os executáveis encontrados**:
  ```bash
  type -a comando
  ```
- **Apps baixados manualmente** → Coloque em:
  - `~/apps/meuapp/bin` (e adicione ao PATH), ou  
  - `~/.local/bin` (já costuma estar no PATH).  

---

✅ **Resumo rápido**
- `PATH` = mapa de onde o sistema busca comandos.  
- Ordem importa → o **primeiro encontrado** ganha prioridade.  
- Adicione diretórios com `export PATH=...`.  
- Para ser permanente → edite `~/.bashrc` ou `~/.zshrc`.  
- Use `which` e `type -a` para saber qual executável está sendo usado.  
