# 🛒 Checkout Personal Trainer

Página de checkout externa para o Personal Trainer App.

## 🚀 Deploy no Vercel (5 minutos)

### Passo 1: Criar repositório no GitHub

1. Acesse [github.com](https://github.com)
2. Clique em **"New repository"**
3. Nome: `checkout-personal`
4. Deixe **público**
5. Clique **"Create repository"**

### Passo 2: Fazer upload dos arquivos

1. No repositório criado, clique em **"uploading an existing file"**
2. Arraste os 3 arquivos:
   - `index.html`
   - `vercel.json`
   - `README.md`
3. Clique **"Commit changes"**

### Passo 3: Conectar no Vercel

1. Acesse [vercel.com](https://vercel.com)
2. Clique em **"Sign Up"** → **"Continue with GitHub"**
3. Autorize o acesso
4. Clique em **"Add New..."** → **"Project"**
5. Selecione o repositório `checkout-personal`
6. Clique **"Deploy"**
7. Aguarde 30 segundos... ✅ Pronto!

### Passo 4: Acessar o checkout

Sua URL será algo como:
```
https://checkout-personal.vercel.app
```

Para acessar um produto:
```
https://checkout-personal.vercel.app/rafael-personal?produtoId=995cd7fd-320d-492d-850c-d3f2ea50a34b
```

## 🔧 Configuração

A configuração está no início do arquivo `index.html`:

```javascript
const SUPABASE_URL = 'https://htdvkqlmshpiterrwacp.supabase.co';
const SUPABASE_ANON_KEY = 'sua-anon-key-aqui';
```

## 📱 Funcionalidades

- ✅ Design responsivo (mobile-first)
- ✅ Cores e logo dinâmicas (white-label)
- ✅ Cartão de crédito com parcelas
- ✅ PIX com QR Code
- ✅ Boleto
- ✅ Máscaras de input (CPF, telefone, cartão)
- ✅ Preview do cartão em tempo real
- ✅ Validação de formulário
- ✅ Páginas de resultado (sucesso/pendente/erro)

## 🔗 URL Structure

```
/{slug}?produtoId={id}
```

- `slug`: Identificador do personal (ex: `rafael-personal`)
- `produtoId`: UUID do produto no banco

## 📊 Fluxo

1. Usuário acessa URL com slug e produtoId
2. Página busca dados na `view_checkout` do Supabase
3. Renderiza checkout com logo e cores do personal
4. Usuário preenche dados e escolhe forma de pagamento
5. Ao clicar "Pagar", chama Edge Function `criar-cobranca`
6. Mostra página de resultado conforme resposta

## 🎨 Customização

As cores são aplicadas via CSS Variables:

```css
:root {
    --primary-color: #6366F1;
    --secondary-color: #10B981;
}
```

As cores são sobrescritas dinamicamente com base nos dados do `view_checkout`:
- `primary_color` → `--primary-color`
- `secondary_color` → `--secondary-color`

## 🔒 Segurança

- A anon key do Supabase é pública (por design)
- RLS protege os dados no Supabase
- Dados do cartão são enviados diretamente para o Pagar.me via Edge Function
- Nenhum dado sensível é armazenado no frontend

## 📞 Suporte

Em caso de dúvidas, entre em contato com o desenvolvedor.
