# Funções Básicas para Python

Este repositório contém um pequeno conjunto de utilitários que eu uso em praticamente todos os meus projetos Python. O arquivo principal é `funcoesBasicas.py` e reúne funções para configuração de logging, formatação de texto no terminal, limpeza da tela e pequenas pausas no fluxo do programa.

## Arquivo

- `funcoesBasicas.py` — implementa as funções mostradas abaixo.

## Funções incluídas

- `logging_config(nomeArquivo)`
  - Configura o sistema de logging do Python para gravar logs em um diretório `logs` localizado no mesmo diretório do script em execução. Chame passando `__file__` ou uma string qualquer para nomear o arquivo de log.
  - Gera um arquivo de log com timestamp e envia a saída também para stdout.

 - `textoCor(texto: str, cor: Cor = Cor.VERMELHO)`
  - Pinta o texto usando a enum `Cor` definida em `funcoesBasicas.py`. Exemplos de membros: `Cor.VERDE`, `Cor.VERMELHO_CLARO`, `Cor.FUNDO_AZUL`.
  - Retorna uma string com códigos ANSI aplicados. Usar a enum facilita autocomplete e evita passar códigos numéricos "mágicos".
  - Observação: em alguns terminais Windows antigos pode ser necessário habilitar o suporte a ANSI.

- `limpar()`
  - Limpa o terminal usando `cls` no Windows e `clear` em outros sistemas.

- `pausa(time: float = 0.5)`
  - Pausa a execução por `time` segundos (usa `time.sleep`).

## Exemplos de uso

Exemplo mínimo em um script `meu_script.py`:

```python
from funcoesBasicas import logging_config, textoCor, limpar, pausa, Cor

if __name__ == '__main__':
    logging_config(__file__)  # cria logs/Meuscript_DD-MM-YYYY_HHh-MMm-SSs.log
    # Exemplo usando enum Cor
    print(textoCor('Iniciando processo...', Cor.VERDE))
    # Exemplo com cor de fundo
    print(textoCor('Aviso: operação lenta', Cor.FUNDO_AMARELO))
    pausa(1)
    limpar()
    print('Pronto')
```

Observações:

- O `logging_config` cria automaticamente a pasta `logs` ao lado do script em execução. Os logs são gravados em UTF-8.
- A função `textoCor` usa sequências ANSI. Terminais modernos (Windows 10+, PowerShell/Windows Terminal, Linux, macOS) suportam essas sequências por padrão. Em versões antigas do Windows pode ser necessário habilitar `VT100` ou usar um helper para cores.

## Compatibilidade

As funções foram escritas para serem simples e portáveis. São adequadas para scripts utilitários e projetos pequenos.

## Licença

Sinta-se à vontade para usar ou adaptar estas funções em seus projetos pessoais e profissionais.
