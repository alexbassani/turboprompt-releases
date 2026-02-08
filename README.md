# TurboPrompt Releases — Manual Completo

> **O que é este repositório?**
> É um repositório PÚBLICO no GitHub que serve como "quadro de avisos" para as extensões TurboPrompt.
> Ele contém UM ÚNICO arquivo importante: `latest.json`.
> As extensões dos alunos consultam esse arquivo silenciosamente para saber se há atualização.

---

## ⛔ REGRAS IMPORTANTES

```
1. Este repositório é PÚBLICO — qualquer pessoa pode ver o latest.json
2. O latest.json NÃO contém código — apenas versões e mensagens
3. As extensões NÃO se atualizam automaticamente — apenas INFORMAM o aluno
4. NUNCA colocar código, senhas, chaves de API ou dados sensíveis aqui
5. O único arquivo que importa é o latest.json — não precisa de mais nada
```

---

## Como funciona (visão geral)

```
Você edita latest.json → push no GitHub → extensão do aluno consulta → mostra popup se tiver atualização
```

Mais detalhado:
1. As extensões TurboPrompt verificam **silenciosamente** (a cada 6h) o `latest.json` deste repositório
2. Se a versão no `latest.json` for **maior** que a versão instalada, um popup amigável aparece
3. O aluno pode: **Baixar Atualização** (vai para Kiwify) | **Lembrar depois (24h)** | **Fechar**
4. Se as versões forem iguais → **não mostra nada**
5. Se o check falhar (sem internet, etc.) → **não mostra nada** (nunca bloqueia)

---

## Como notificar os alunos sobre uma atualização

### Passo a passo (para humanos):

```
1. Abrir o arquivo latest.json (aqui neste repositório)
2. Encontrar a extensão que você atualizou
3. Mudar o número da "version" para a versão nova
4. Mudar a "message" para descrever o que mudou (opcional)
5. Commit e push
6. PRONTO. Os alunos verão o popup em até 6 horas.
```

### Exemplo prático:

Digamos que você atualizou o META AI FULL para a versão 5.4.0.

**Antes:**
```json
"meta-ai-full": {
  "version": "5.3.3",
  "message": "Melhorias de segurança e sistema de notificação de atualizações."
}
```

**Depois:**
```json
"meta-ai-full": {
  "version": "5.4.0",
  "message": "Nova funcionalidade de download em lote adicionada!"
}
```

Commit, push, e pronto. Os alunos que tiverem a versão 5.3.3 instalada verão o popup.

---

## Passo a passo (para IA / assistente de código):

> Se o usuário pedir para "notificar os alunos", "publicar atualização", "avisar sobre nova versão",
> ou qualquer frase parecida, siga EXATAMENTE este fluxo:

```bash
# 1. Ir para o repositório turboprompt-releases
#    Clone local: D:\_Projetos\turboprompt\_releases
#    (clone do repo github.com/alexbassani/turboprompt-releases dentro do repo principal)

# 2. Editar o latest.json:
#    - Alterar "version" da extensão para a versão nova
#    - Alterar "message" com descrição da atualização
#    - Alterar "updatedAt" para a data atual (formato YYYY-MM-DD)

# 3. Commit e push
git add -A
git commit -m "release: notificar atualização <extensão> v<versão>"
git push origin main

# 4. Confirmar que o push foi feito
# 5. Informar o usuário que os alunos serão notificados em até 6h
```

### IMPORTANTE para IA:
- **NÃO** precisa criar tags no GitHub
- **NÃO** precisa criar releases no GitHub
- **NÃO** precisa fazer upload de arquivos
- **NÃO** precisa mexer no repositório turboprompt (main)
- Basta editar o `latest.json`, commit e push. **Só isso.**

---

## Estrutura do `latest.json`

```json
{
  "updatedAt": "2026-02-07",
  "kiwifyUrl": "https://pay.kiwify.com.br/UN9kn6X",
  "extensions": {
    "nome-da-extensao": {
      "version": "X.Y.Z",
      "message": "Descrição da atualização para o aluno."
    }
  }
}
```

| Campo | O que é | Quando mudar |
|---|---|---|
| `updatedAt` | Data da última atualização | Sempre que editar qualquer versão |
| `kiwifyUrl` | Link da Kiwify para o aluno baixar | Só se o link mudar |
| `version` | Versão mais recente da extensão | Quando lançar versão nova |
| `message` | Texto que aparece no popup do aluno | Quando quiser mudar a mensagem |

### IDs das extensões (usar exatamente estes nomes):

| ID no latest.json | Extensão |
|---|---|
| `autowhisk` | TurboPrompt AutoWhisk |
| `grok-animator` | TurboPrompt GROK Animator |
| `imagefx` | TurboPrompt ImageFX |
| `meta-ai-basic` | TurboPrompt META AI Basic |
| `meta-ai-full` | TurboPrompt META AI FULL |
| `piclumen` | TurboPrompt PicLumen |
| `sora` | TurboPrompt Sora |
| `turboflow` | TurboPrompt TurboFlow |
| `turboprompt-veo3` | TurboPrompt VEO3 Video Generator |

---

## URL usada pelas extensões

```
https://raw.githubusercontent.com/alexbassani/turboprompt-releases/main/latest.json
```

As extensões fazem um `fetch` nesta URL a cada 6h. Não precisa configurar nada — já está embutido em cada popup.js.

---

## Perguntas frequentes

**P: Preciso criar uma tag ou release no GitHub?**
R: NÃO. Basta editar o `latest.json` e fazer push.

**P: E se eu errar a versão no latest.json?**
R: Se colocar uma versão MAIOR que a instalada, o popup aparece. Se colocar IGUAL ou MENOR, não aparece. Basta corrigir e fazer push de novo.

**P: O aluno vai ser obrigado a atualizar?**
R: NÃO. O popup é apenas informativo. O aluno pode fechar ou ignorar.

**P: E se o aluno não tiver internet?**
R: O check falha silenciosamente. Não mostra nada, não bloqueia nada.

**P: Posso notificar só UMA extensão?**
R: SIM. Basta mudar a versão apenas daquela extensão no latest.json.

**P: Quanto tempo demora para o aluno ver a notificação?**
R: Até 6 horas após o push. Na próxima vez que o aluno abrir o popup da extensão.
