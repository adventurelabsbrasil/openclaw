# openclaw

Repositório para o projeto **OpenClaw** no Vercel — usado para configurar o subdomínio que aponta ao OpenClaw hospedado no Railway.

## Deploy no Vercel

1. Conecte este repositório no [Vercel](https://vercel.com): **Add New Project** → **Import Git Repository** → selecione `openclaw`.
2. Faça o deploy (o projeto é estático; não precisa de build).

## Configurar o subdomínio para o Railway

Para que um subdomínio (ex.: `openclaw.seudominio.com`) aponte para o **OpenClaw no Railway**, configure o DNS no provedor do domínio (ex.: Vercel Domains, Cloudflare, Registro.br).

### No Vercel (se o domínio estiver no Vercel)

1. Vercel → **Domains** (ou no projeto → **Settings** → **Domains**).
2. Adicione o domínio raiz se ainda não estiver.
3. Adicione o **registro DNS** para o subdomínio (não use “Assign to project” se quiser que o tráfego vá para o Railway):

| Tipo  | Nome                    | Valor / Destino           |
|-------|-------------------------|---------------------------|
| **CNAME** | `openclaw`           | `uh1yzdcn.up.railway.app` |
| **TXT**   | `_railway-verify.openclaw` | `railway-verify=3f939a8b99ee803c179709e15661cad8f6a5c6a02771b9a8e4166a844ce0e18b` |

Assim o subdomínio resolve para o serviço OpenClaw no Railway e o Railway consegue verificar a propriedade do domínio.

### Em outros provedores DNS

- **CNAME:** host `openclaw` (ou o subdomínio desejado) → `uh1yzdcn.up.railway.app`.
- **TXT:** host `_railway-verify.openclaw` → valor completo `railway-verify=3f939a8b99ee803c179709e15661cad8f6a5c6a02771b9a8e4166a844ce0e18b`.

Após a propagação, acesse: `https://openclaw.seudominio.com/openclaw` (Control UI) e `https://openclaw.seudominio.com/setup` (wizard).
