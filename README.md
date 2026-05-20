# 🎮 Jogos de Adivinhação - Coleção Python

Uma coleção completa de jogos de adivinhação desenvolvidos em Python, com ranking persistente, mecânicas dinâmicas e integração com APIs externas.

> **Status:** ✅ Em manutenção | **Python:** 3.8+ | **Licença:** MIT

---

## 📚 Sumário

- [Sobre os Projetos](#sobre-os-projetos)
- [Instalação](#instalação)
- [Projetos Disponíveis](#projetos-disponíveis)
- [Como Jogar](#como-jogar)
- [Estrutura Técnica](#estrutura-técnica)
- [Arquivos Gerados](#arquivos-gerados)

---

## 🎯 Sobre os Projetos

Este repositório contém **2 projetos independentes** de jogos de adivinhação, cada um com suas próprias mecânicas e desafios:

| Projeto | Tipo | Dificuldade | API | Ranking |
|---------|------|------------|-----|---------|
| **Adivinhação Clássica** | Números + Cartas | 🟡 Médio | Nenhuma | `ranking.json` |
| **Magic: The Gathering** | Cartas Reais MTG | 🔴 Difícil | Scryfall | `ranking_magic.json` |

---

## 🚀 Instalação

### Pré-requisitos

```bash
python --version  # 3.8 ou superior
pip --version     # gerenciador de pacotes
```

### Clonar Repositório

```bash
git clone https://github.com/Deziderio55/Jogos-de-Adivinhacao.git
cd Jogos-de-Adivinhacao
```

### Instalar Dependências

**Adivinhação Clássica** (sem dependências externas):
```bash
# Nenhuma dependência necessária - usa apenas stdlib
python JogoDaAdivinhaçãoCartaz.py
```

**Magic: The Gathering** (com dependências):
```bash
pip install requests  # Necessário para requisições HTTP à API Scryfall
python Magic_O_Ajuntamento.py
```

---

## 📦 Projetos Disponíveis

### 🎲 Projeto 1: Adivinhação Clássica

**Arquivo:** `JogoDaAdivinhaçãoCartaz.py`

Jogo com **dois modos** diferentes em um único arquivo.

#### 🔢 Modo 1: Adivinhação de Números

```
Mecânica:
├─ Número sorteado: 1 a 100
├─ Tentativas: até 10
├─ Feedback: maior/menor
└─ Pontuação máxima: 1000 pts (reduz 80 por tentativa extra)
```

**Como jogar:**
1. Execute o programa
2. Escolha "Modo Números"
3. Digite um número entre 1 e 100
4. Receba dica se errar (maior ou menor)
5. Ganhe pontos ao acertar!

---

#### 🃏 Modo 2: Adivinhação de Cartas

```
Mecânica:
├─ Carta sorteada: 52 cartas (baralho padrão)
├─ Tentativas: até 6
├─ Feedback: maior/menor + naipe
└─ Pontuação máxima: 1200 pts (reduz 150 por tentativa extra)
```

**Formato de entrada:**

```
<Valor> <Naipe>

Valores válidos: A, 2-10, J, Q, K
Naipes válidos: Copas, Ouros, Espadas, Paus

Exemplos:
  A Copas
  10 Espadas
  J Paus
  5 Ouros
```

---

### ☀️💧☠️🔥🌳 Projeto 2: Magic: The Gathering

**Arquivo:** `Magic_O_Ajuntamento.py`

Jogo avançado usando cartas **reais** do MTG via API Scryfall em tempo real.

#### 🎴 Características

```
Geral:
├─ Tentativas: até 8
├─ Dicas: 8 progressivas (automáticas a cada erro)
├─ Pontuação: 1000 - (tentativas - 1) × 80 - dicas × 40 (mín. 50)
├─ Ranking: salvo em ranking_magic.json
└─ API: Scryfall (100% cartas reais do MTG)
```

#### 🎮 Modos de Jogo

**1️⃣ Qualquer Carta (Padrão)**
```
Busca aleatória em todo o banco de dados Scryfall
└─ Ideal para: desafio máximo
```

**2️⃣ Coleção Específica**
```
Escolha um set (coleção) de MTG
└─ Exemplos: dsk, mkm, ltr, m21, znr, mid
└─ Ideal para: focar em cartas conhecidas
```

**3️⃣ Intervalo Entre Coleções**
```
Escolha data inicial e final para filtrar cartas
└─ Exemplos: "m21" até "mid" = cartas desse período
└─ Ideal para: explorar épocas específicas do jogo
```

#### 💡 Sistema de Dicas Progressivas

| Ordem | Dica | Exemplo |
|-------|------|---------|
| 1ª | Cores da carta | "Azul, Preto" |
| 2ª | Tipo | "Criatura — Vampiro" |
| 3ª | Raridade | "Rara" |
| 4ª | Custo de mana | CMC: 5 |
| 5ª | Conjunto | "Dominaria United" |
| 6ª | Poder/Resistência | "3 / 4" (se criatura) |
| 7ª | Trecho de texto | Primeiras palavras da descrição |
| 8ª | Imagem oficial | Link da carta no Scryfall |

#### ⌨️ Comandos Especiais

| Comando | Efeito |
|---------|--------|
| `!dica` | Pedir dica antecipada (custa 40 pontos) |
| `!desistir` | Revelar carta e encerrar (0 pontos) |

#### 🔍 Autocomplete

Enquanto digita, o jogo sugere nomes de cartas:
```
> "Bol"
Sugestões: Bolt, Boletus, Bolan...
```

---

## 🎮 Como Jogar

### Adivinhação Clássica

```bash
python JogoDaAdivinhaçãoCartaz.py

Menu Principal:
1 - Jogar
2 - Ver Ranking
3 - Sair

# Após escolher modo:
# Digite seu palpite e receba feedback!
```

### Magic: The Gathering

```bash
python Magic_O_Ajuntamento.py

Menu Principal:
1 - Jogar
2 - Ver Ranking
3 - Sair

# Após escolher modo de coleção:
# 1 - Qualquer carta
# 2 - Coleção específica (ex: dsk)
# 3 - Intervalo (ex: m21 até mid)

# Durante o jogo:
# Digite o nome da carta ou use !dica / !desistir
```

---

## 📊 Sistema de Ranking

Ambos os jogos mantêm ranking persistente em JSON:

### Ranking Clássico (`ranking.json`)

```json
[
  {
    "nome": "Jogador1",
    "modo": "Números",
    "pontuacao": 950,
    "tentativas": 3,
    "data": "20/05/2026 14:30"
  }
]
```

### Ranking Magic (`ranking_magic.json`)

```json
[
  {
    "nome": "Planeswalker",
    "carta": "Black Lotus",
    "pontuacao": 800,
    "tentativas": 2,
    "data": "20/05/2026 15:45"
  }
]
```

**Ordenação:** Por pontuação (maior primeiro) → tentativas (menor primeiro)

---

## 🏗️ Estrutura Técnica

### Arquitetura

Ambos os projetos seguem **princípios SOLID** e **OOP**:

```
├─ Classe abstrata Jogo
│  ├─ iniciar()  → exibe menu/instruções
│  └─ jogar()    → lógica principal
│
├─ Classe Ranking
│  ├─ registrar()  → salva partida em JSON
│  ├─ exibir()     → mostra ranking formatado
│  └─ carregar()   → lê dados persistidos
│
├─ Classes específicas de jogo
│  ├─ JogoNumeros
│  ├─ JogoCartas
│  └─ JogoMagic
│
└─ API Scryfall (Magic apenas)
   ├─ carta_aleatoria()
   ├─ autocomplete()
   └─ listar_colecoes()
```

### Padrões de Design

| Padrão | Uso |
|--------|-----|
| **Abstract Factory** | Classe `Jogo` define interface |
| **Strategy** | Diferentes modos como estratégias |
| **Singleton** | Classe `Ranking` gerencia estado |
| **Encapsulation** | Atributos privados com `__` |

### Principais Classes

```python
# Classe abstrata base
class Jogo(ABC):
    @abstractmethod
    def iniciar(self): pass
    
    @abstractmethod
    def jogar(self): pass

# Gerencia persistência
class Ranking:
    def registrar(nome, pontos, tentativas, extra): ...
    def exibir(self): ...

# API Scryfall (Magic)
class ScryfallAPI:
    @staticmethod
    def carta_aleatoria() -> dict: ...
    @staticmethod
    def autocomplete(prefixo: str) -> list: ...
```

---

## 📋 Requisitos

| Projeto | Python | Dependências | Conexão |
|---------|--------|--------------|---------|
| **Clássico** | 3.8+ | Nenhuma (stdlib) | ❌ Não precisa |
| **Magic** | 3.10+ | `requests` | ✅ Requer internet |

---

## 📁 Arquivos do Repositório

```
Jogos-de-Adivinhacao/
├─ JogoDaAdivinhaçãoCartaz.py      # Projeto 1: Números + Cartas
├─ JogoDaAdivinhaçãoMagic.py       # Versão alternativa (deprecated)
├─ Magic_O_Ajuntamento.py          # Projeto 2: MTG (versão atual)
├─ README.md                        # Este arquivo
└─ ranking_*.json                   # Gerados em runtime
```

### 📊 Arquivos Gerados em Runtime

Ao jogar, os seguintes arquivos são criados:

```
ranking.json          # Histórico completo do jogo clássico
ranking_magic.json    # Histórico completo do jogo Magic
```

**Formato:** JSON UTF-8 | **Localização:** Diretório raiz

---

## 🔒 Considerações de Segurança

- ✅ Validação de entrada do usuário (máx 100 caracteres)
- ✅ Tratamento robusto de JSON corrompido
- ✅ Retry automático em falhas de conexão (3 tentativas)
- ✅ Timeout configurado para requisições (5 segundos)
- ✅ Sem armazenamento de credenciais sensíveis

---

## 🚀 Futuros Melhoramentos

- [ ] Suporte a multiplayer online
- [ ] Banco de dados ao invés de JSON
- [ ] Interface gráfica (tkinter/pygame)
- [ ] Estatísticas e gráficos de desempenho
- [ ] Sistema de achievements/badges
- [ ] Modo time/cooperativo

---

## 🤝 Contribuindo

Encontrou um bug ou tem uma ideia? Abra uma **issue**!

```bash
# Passos:
1. Faça fork do repositório
2. Crie uma branch (git checkout -b feature/sua-ideia)
3. Commit suas mudanças (git commit -m "descrição")
4. Push para a branch (git push origin feature/sua-ideia)
5. Abra um Pull Request
```

---

## 📝 Licença

Este projeto está sob a licença **MIT**. Veja [LICENSE](LICENSE) para detalhes.

---

## 👨‍💻 Autor

**Deziderio55**  
GitHub: [@Deziderio55](https://github.com/Deziderio55)

---

## 🎯 Créditos

- **Scryfall API:** https://scryfall.com/docs/api
- **Magic: The Gathering:** Wizards of the Coast

---

## 📞 Suporte

Dúvidas? Abra uma **issue** ou envie um **email**!

---

**Última atualização:** 20 de maio de 2026  
**Versão:** 2.0 (com melhorias de segurança)
