# Aniversários → Google Agenda (Apps Script)

Ferramenta simples e robusta para criar eventos de **aniversário** como **dia todo** no Google Agenda a partir de uma planilha Google Sheets.

## ✨ Recursos
- Menu e sidebar com botão **“Enviar para Agenda”**.
- **Deduplicação resiliente** via marcador oculto no *Description* do evento (evita duplicatas mesmo com títulos iguais).
- **Ajuste automático de 29/fev** em anos não bissextos (mapeia para 28/fev).
- Logs de processamento no **Executions → Logs**.
- Suporte a **calendário padrão** ou **ID customizado**.

## 🧱 Estrutura da planilha
- **Coluna A**: Nome (ex.: `Maria Oliveira`)
- **Coluna B**: Data de nascimento (ex.: `15/08/1999` ou `1999-08-15`)

> Dica: deixe uma linha de cabeçalho na linha 1.

## 🚀 Como usar
1. Abra a planilha com os dados.
2. Vá em **Extensões → Apps Script** e cole o conteúdo de `src/aniversarios.gs`.
3. (Opcional) Em `ANIV.CALENDAR_ID`, defina o ID de um calendário específico; se deixar `null`, usa o padrão da sua conta.
4. Salve. Volte à planilha e use o menu **Aniversários → Enviar para Agenda** (ou **Abrir botão (Sidebar)**).

## 🔐 Permissões
Na primeira execução, o Apps Script pedirá autorização para acessar seu calendário e planilha.

## 🧪 Deduplicação — como funciona
O script gera um **ID estável** por aniversário (nome normalizado + dia/mês do evento) e grava um marcador oculto no **Description** do evento. Antes de criar, ele verifica se já existe um evento do mesmo dia com esse marcador. Assim, **não cria duplicatas** se rodar novamente.

## 🛠️ Ajustes úteis
- **Calendário específico**: preencha `ANIV.CALENDAR_ID` com o ID do seu calendário.
- **Prefixo do título**: edite `TITLE_PREFIX` se quiser outro texto (ex.: `Aniv. `).

## 📝 Limitações
- O evento é lançado **apenas para o ano atual** (intencional para evitar enchentes de eventos futuros).
- Datas inválidas ou células vazias são **puladas** e relatadas no resumo.

## 🗂️ Estrutura sugerida do repositório
