# TurboPrompt Releases

Repositório público usado pelas extensões TurboPrompt para verificar se há atualizações disponíveis.

## Como funciona

1. As extensões TurboPrompt verificam silenciosamente (a cada 6h) o arquivo `latest.json` deste repositório
2. Se a versão no `latest.json` for maior que a versão instalada, um popup amigável é exibido ao usuário
3. O usuário pode fechar o popup ou clicar para baixar a atualização na Kiwify

## Arquivo `latest.json`

Contém a versão mais recente de cada extensão e uma mensagem opcional.

### Como atualizar

Edite o `latest.json` e altere a versão e/ou mensagem da extensão desejada:

```json
{
  "extensions": {
    "meta-ai-full": {
      "version": "5.3.2",
      "message": "Nova funcionalidade X adicionada!"
    }
  }
}
```

Faça commit e push. As extensões dos alunos detectarão a mudança automaticamente na próxima verificação (até 6h).

## URL usada pelas extensões

```
https://raw.githubusercontent.com/alexbassani/turboprompt-releases/main/latest.json
```

## Importante

- Este repositório é **público** — qualquer pessoa pode ver o `latest.json`
- O `latest.json` **NÃO contém código** — apenas versões e mensagens
- As extensões **NÃO se atualizam automaticamente** — apenas informam o aluno
