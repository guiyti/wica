# WICA 2025 — Componente de Cronograma

Componente front-end simples e responsivo para exibir o cronograma do WICA (Universidade Cruzeiro do Sul).

- HTML/CSS puro + JavaScript leve (sem frameworks)
- Estilos encapsulados e prontos para "copiar e colar" (usa Tailwind via CDN e CSS inline)
- Dados externos em JSON (sem build, sem backend)
- Responsivo: 1/2/4 colunas (mobile/tablet/desktop)
- Badges de modalidade: Remoto (link do Teams) ou Presencial (Campus)

## Demo local
Por causa do fetch do arquivo JSON, abra o projeto em um servidor estático (acessar via file:/// pode bloquear a leitura do JSON em alguns navegadores).

- Python 3
```bash
python3 -m http.server 5173
# em seguida abra http://localhost:5173/wica.html
```

- Node.js (opcional)
```bash
npx serve . -l 5173 --single
# em seguida abra http://localhost:5173/wica.html
```

## Estrutura do projeto
```
.
├── wica.html         # Componente (HTML/CSS/JS) e layout responsivo
├── wica-data.json    # Fonte de dados (eventos)
├── logo.png          # Logo usado no hero
└── README.md         # Este arquivo
```

## Como editar o cronograma (JSON)
Todos os eventos são carregados de wica-data.json. Exemplo de item:

```json
{
  "date": "2025-10-13",
  "dateLabel": "13/10 - Segunda-feira",
  "period": "manhã",
  "time": "9h às 10h30",
  "speaker": "Nome do Palestrante",
  "title": "Criando uma Plataforma de BI - 100% Open Source.",
  "modality": "presencial",
  "campus": "São Miguel",
  "tags": ["EMPRESA", "HANDS-ON"]
}
```

Campos:
- date (ISO, opcional para ordenação futura)
- dateLabel (ex.: "13/10 - Segunda-feira")
- period (ex.: manhã ou noite) — exibido no badge de horário
- time (ex.: 9h às 10h30)
- speaker (nome do palestrante)
- title (título/tema da palestra)
- modality (remoto | presencial)
  - Se remoto: informar teamsUrl (link da sala)
  - Se presencial: informar campus
- tags (array de rótulos curtos, ex.: EMPRESA, HANDS-ON, etc.)

Campi válidos (presencial):
- São Miguel, Villa Lobos, Guarulhos, Santo Amaro, Anália Franco, Liberdade, Paulista

## Layout e responsividade
- Grid: 1 coluna (mobile), 2 colunas (md), 4 colunas (lg e acima)
- Hero simples com logo, nome da universidade e título do evento
- Badges:
  - Horário: verde (.time-badge)
  - Data: dourado (.date-time-badge)
  - Remoto: roxo (.badge-remote) com link para o Teams
  - Presencial: laranja/vermelho (.badge-inperson) com nome do Campus

## Personalização rápida
- Cores/gradientes dos badges: edite as classes .date-time-badge, .time-badge, .badge-remote, .badge-inperson em wica.html
- Colunas: ajuste as classes grid-cols-* do container #schedule-grid
- Tipografia: fonte via Google Fonts (Inter) e utilitários do Tailwind (CDN)

## Embutir em outro site
1. Copie o bloco do componente de wica.html (incluindo <link> de fontes, <style> e o <script> que carrega o JSON)
2. Garanta que wica-data.json esteja acessível no mesmo domínio/caminho (ou ajuste a URL do fetch)
3. Atualize o caminho de logo.png se necessário

## Deploy (GitHub Pages)
1. Faça commit de wica.html, wica-data.json, logo.png e README.md
2. Em Settings → Pages, selecione a branch e a pasta raiz
3. Acesse a URL publicada (https://<seu-usuario>.github.io/<repo>/wica.html)

## Roadmap (sugestões)
- Ordenação automática por data/horário
- Filtros (por dia, período, modalidade)
- Destaque de trilhas/salas

## Licença
Defina a licença conforme necessidade do projeto (ex.: MIT).
