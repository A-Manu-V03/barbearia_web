# Documentação do Login — AV2

## Funcionamento do login

A Barbearia Web utiliza a API DummyJSON para realizar uma autenticação demonstrativa com usuários fictícios.

Na página `/login`, o usuário informa suas credenciais. Antes de enviar a requisição, o sistema verifica se os campos obrigatórios foram preenchidos.

A autenticação é realizada pelo serviço `authService.login`, que utiliza `fetch` para enviar uma requisição à API.

Quando as credenciais são válidas, os dados básicos do usuário e o token de acesso são encaminhados ao `AuthContext`, responsável pelo gerenciamento da sessão.

Após a autenticação, o usuário é redirecionado para a página que tentou acessar anteriormente ou para `/painel`.

## Contrato da API

| Item | Descrição |
|---|---|
| API | DummyJSON |
| Endpoint | `POST https://dummyjson.com/auth/login` |
| Formato | JSON |
| Dados enviados | `username`, `password`, `expiresInMins` |
| Dados utilizados | `accessToken` e informações básicas do usuário |
| Validação da sessão | `GET https://dummyjson.com/auth/me` |
| Autorização | `Authorization: Bearer <accessToken>` |

**Credenciais demonstrativas:** `emilys` / `emilyspass`.

## Tratamento de erros

O sistema apresenta mensagens específicas para diferentes situações:

- Campos vazios: solicita o preenchimento antes de chamar a API.
- Credenciais inválidas: informa que o usuário ou a senha estão incorretos.
- Falha de conexão: orienta verificar a internet.
- Acesso não autorizado: apresenta mensagem apropriada.
- Sessão expirada: solicita uma nova autenticação.

## Gerenciamento da sessão

O sistema utiliza `sessionStorage` para armazenar temporariamente o token e os dados básicos do usuário, sem armazenar a senha.

A sessão pode ser restaurada após atualizar a página. Quando o token é rejeitado durante a verificação, o usuário é direcionado para o login.

O logout remove a sessão local.

A proteção das rotas ocorre na interface React e não substitui mecanismos de segurança de um servidor.

## Contribuição individual — Emanuele Vitória Lima de Souza

Participei do desenvolvimento da autenticação demonstrativa da Barbearia Web, trabalhando na integração com a API DummyJSON, na tela de login, na validação dos campos e no tratamento de erros.

Também implementei ajustes no redirecionamento de usuários autenticados e na apresentação de mensagens de sessão expirada, além de realizar testes funcionais e ajustes visuais.

Entre as evidências da minha participação estão o PR #22, relacionado à tela de login, e o PR #24, referente às correções de sessão e redirecionamento.

## Uso de inteligência artificial

Utilizei inteligência artificial como ferramenta de apoio durante o desenvolvimento para compreender conceitos de React e JavaScript, analisar o funcionamento do código, receber orientações de implementação e auxiliar na identificação de problemas.

A ferramenta também apoiou a organização dos testes e o aprendizado de comandos Git e GitHub. As alterações foram verificadas por meio de testes manuais e análise estática do código.