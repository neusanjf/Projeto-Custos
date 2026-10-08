# Cadastro de Custos PV

Página de cadastro de funcionários e custos (com vigência mensal) por empresa e unidade.
Os dados ficam na planilha Google **Analise_Custos**, acessada pelo Apps Script.

## Como funciona

- `index.html` é publicado no GitHub Pages.
- A página chama o app da Web do Apps Script (função `doPost` no `Code.gs`), que lê e grava nas abas
  `Unidades`, `Funcionarios` e `Custos`, registra o `Historico` e recalcula as abas `Base_*`.
- O acesso é protegido por senha. O token de sessão vale 6 horas.

## Publicar

1. **Apps Script**: cole o `Code.gs` atualizado no projeto vinculado à planilha e salve.
2. **Implantar › Gerenciar implantações › editar (lápis)**:
   - Versão: **Nova versão**
   - Executar como: **Eu**
   - Quem pode acessar: **Qualquer pessoa**
   A URL `/exec` continua a mesma.
3. **GitHub**: crie um repositório, envie `index.html` e este `README.md` para a branch `main`.
4. **Settings › Pages › Build and deployment**: Source *Deploy from a branch*, branch `main`, pasta `/ (root)`.
   O site fica em `https://<usuario>.github.io/<repositorio>/`.

Se a URL do Apps Script mudar, atualize a constante `API_URL` no `index.html`.

## Segurança

O GitHub Pages é público, e a implantação “Qualquer pessoa” permite que qualquer um chame a API.
O que protege os dados é a senha: sem ela, nenhuma função de leitura ou gravação responde.
Após 5 tentativas erradas, o acesso fica bloqueado por 10 minutos.
Use uma senha forte e troque-a pela página ou pelo menu **Custos PV › Redefinir senha** na planilha.
