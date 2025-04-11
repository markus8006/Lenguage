# Lenguage
Para fins de estudo, estou criando uma linguagem
# 🧠 Mini Interpretador de Linguagem Simples em Python

Este projeto implementa um pequeno interpretador de uma **linguagem fictícia**, capaz de:

- Declarar variáveis do tipo **Texto**, **Número** e **Decimal**
- Executar comandos como `Diga` para imprimir mensagens
- Armazenar variáveis em um dicionário com tipo e valor
- Suportar **modo de depuração (debug)** para visualizar os valores das variáveis

---

## 📂 Estrutura do Projeto

### 📌 Função principal

#### `interprete(code, vars, debug=False)`
Interpreta uma sequência de comandos simples.

- **code**: código em forma de string (ex: `"x = 2
  Diga('Olá')"`)
- **vars**: dicionário de variáveis compartilhado
- **debug**: se `True`, exibe as variáveis ao final da execução

### 🧱 Classes

#### `class Texto`
Cria uma variável do tipo **Texto** (string entre aspas simples).
```python
Texto("nome", "'João'", vars)
```

#### `class Numero`
Cria uma variável do tipo **Número** (inteiro).
```python
Numero("idade", 20, vars)
```

#### `class Decimal`
Cria uma variável do tipo **Decimal** (valor que será interpretado como decimal, mesmo se string).
```python
Decimal("altura", "1.75", vars)
```

#### `class Main`
Gerenciador principal da execução.
- Recebe o código a ser interpretado
- Executa com ou sem debug

##### Exemplo de uso:
```python
codigo = "x = 10 y = 'teste' Diga'Olá Mundo'"
dex = Main(codigo, debug=True)
dex.run()
```

---

## 💬 Comandos da linguagem

| Comando       | Exemplo                   | Ação                                       |
|---------------|---------------------------|--------------------------------------------|
| Atribuição `=`| `x = 10` ou `y = 'abc'`   | Cria variáveis de tipo número ou texto     |
| `Diga`        | `Diga('Olá Mundo')`       | Exibe a mensagem entre aspas               |

---

## 🔍 Exemplo Completo

```python
codigo = """
"nome = 'Ana'
idade = 18
Diga('Bem-vinda')
"""
dex = Main(codigo, debug=True)
dex.run()
```

📤 **Saída:**
```
Bem-vinda, Ana
{'nome': {'Valor': "'Ana'", 'Tipo': 'Texto'}, 'idade': {'Valor': 18, 'Tipo': 'Numero'}}
```

---

## ⚠️ Observações


- Ver 0.01
- A linguagem é **sensível ao espaço** (não pode haver duplo espaço).
- Aceita apenas aspas simples `'` para `Texto`.
- Não há tratamento de erros sofisticado (ex: sintaxe incorreta ou variáveis indefinidas).
- Funçao Diga() ainda não funcionando corretamente
- Não há lógica matemática

