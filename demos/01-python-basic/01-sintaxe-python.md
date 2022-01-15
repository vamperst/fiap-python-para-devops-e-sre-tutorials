# Sintaxe Python

**Sintaxe Python em comparação com outras linguagens de programação**

- Python foi projetado para ser legível e tem algumas semelhanças com a língua inglesa com influência da matemática.
- Python usa novas linhas para completar um comando, ao contrário de outras linguagens de programação que geralmente usam ponto-e-vírgula ou parênteses.
- Python depende de indentação, usando espaços em branco, para definir o escopo; como o escopo de loops, funções e classes. Outras linguagens de programação costumam usar chaves para esse propósito.

## Indenteção do Python

Enquanto em outras linguagens de programação o recuo no código é apenas para legibilidade, em Python o recuo é muito importante.

Python usa indentação para indicar um bloco de código.

```python
if 5 > 2:
  print("Cinco é maior que dois!")
```

Python apresentará um erro se você pular a indentação.

## Comentários

Python tem capacidade de comentários para fins de documentação no código.

Os comentários começam com `#`, e Python renderizará o resto da linha como um comentário:

```python
#isso é um comentário
print("Hello, World!")
```

## Docstrings

Python também possui capacidade de documentação estendida, chamada docstrings.

Docstrings podem ter uma linha ou várias linhas. Docstrings também são comentários:

Python usa aspas triplas no início e no final da docstring:

```python
"""This is a 
multiline docstring."""
print("Hello, World!")
```

## Referências

- [w3schools.com](https://www.w3schools.com/python/python_syntax.asp)