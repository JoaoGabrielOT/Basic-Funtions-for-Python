# funcoesBasicas

Utilitários portáteis para scripts Python: logging prático, cores ANSI, limpeza de terminal e pausa, todos prontos para uso no terminal moderno.

***

## Instalação

Instale diretamente do PyPI:

```
pip install funcoesBasicas
```

***

## Como usar

Basta importar as funções e a enumeração de cores no seu script:

```
from funcoesBasicas import logging_config, textoCor, limpar, pausa, Cores

if __name__ == '__main__':
    logging_config(__file__)
    print(textoCor('Iniciando processo...', Cores.VERDE))
    # Texto em vermelho claro sobre fundo amarelo
    print(textoCor('Aviso: operação lenta', Cores.VERMELHO_CLARO, Cores.FUNDO_AMARELO))
    pausa(1)
    limpar()
    print('Pronto')
```

***

## Funções disponíveis

- **`logging_config(nomeArquivo)`**:  Configura logging com log file e saída para stdout. Aceita como parâmetro `__file__` ou outro nome.
- **`textoCor(texto: str, cor_texto: Cores = None, cor_fundo: Cores = None)`**:  Retorna o texto com cor ANSI no terminal. Escolha text color e opcionalmente cor de fundo pelo enum `Cores`.
- **`limpar()`**:  Limpa o terminal (funciona em Windows e outros sistemas).
- **`pausa(time: float = 0.5)`**: Pausa o programa por um tempo, padrão 0.5 segundos.
- **Enum `Cores`**: Contém todas as cores disponíveis para texto e fundo, por exemplo: `Cores.VERDE`, `Cores.FUNDO_AZUL_CLARO`, `Cores.AMARELO_CLARO`.

***

## Detalhes técnicos

- `logging_config` cria um diretório `logs` automaticamente junto do script.
- As cores funcionam em terminais modernos (Windows 10+, Linux, macOS). Em versões mais antigas do Windows pode ser necessário habilitar VT100.
- Não há dependências externas.

***

## Compatibilidade

Este pacote foi escrito para scripts e utilitários Python portáteis. 
Funciona em Windows, Linux, macOS e notebooks (Jupyter: cores ANSI podem não aparecer).

***

## Licença

MIT — use livremente em projetos pessoais ou comerciais!
