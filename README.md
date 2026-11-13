# Downloads — Jadlog Robô Faturamento (edição cliente)

Repositório público de **distribuição** do instalador. O código-fonte fica no
repositório privado `jadlog-robo-faturamento`.

## Como o painel cliente se atualiza

1. O painel consulta `latest.json` neste repositório (via `raw.githubusercontent.com`);
2. Compara a versão com a instalada (`APP_VERSION`);
3. Se houver versão mais nova: baixa o instalador da release, confere o SHA-256
   e oferece instalar (instalador em modo silencioso reinicia o painel).

## Como publicar uma versão nova (equipe)

Na pasta do projeto, depois do build:

```powershell
# 1. cria a release com o instalador como anexo
gh release create "v1.6.3" "Playwright/Painel/dist/installer/JadlogRobo-Cliente-Setup-1.6.3.exe" `
  --repo JulyanRaphael/jadlog-robo-faturamento-releases `
  --title "v1.6.3" --notes "Notas da versão..."

# 2. atualiza o latest.json (versão, data, url, sha256, tamanho, changelog) e faz push
```

O hash pode ser conferido com:

```powershell
Get-FileHash .\JadlogRobo-Cliente-Setup-1.6.3.exe -Algorithm SHA256
```

## Formato do `latest.json`

```json
{
  "versao": "1.6.2",
  "data": "2026-11-12",
  "url": "https://github.com/JulyanRaphael/jadlog-robo-faturamento-releases/releases/download/v1.6.2/JadlogRobo-Cliente-Setup-1.6.2.exe",
  "sha256": "...",
  "tamanho": 57746686,
  "changelog": ["item 1", "item 2"]
}
```
