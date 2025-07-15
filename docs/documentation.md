# FastAPI JWT Authentication

Este código é um exemplo de uma aplicação FastAPI que utiliza JWT (JSON Web Tokens) para autenticação de usuários. A autenticação é feita através de um token de acesso que é verificado em cada solicitação.

## Dependências

- FastAPI
- Pydantic
- Passlib
- python-jose
- datetime

## Descrição dos Métodos

### fake_hash_password(password: str)

Cria um hash para a senha do usuário.

#### Parâmetros

- `password: str` - A senha a ser hashada.

### get_user(db, username: str)

Obtém o usuário de um banco de dados fictício.

#### Parâmetros

- `db` - O banco de dados fictício.
- `username: str` - O nome de usuário a ser buscado no banco de dados.

### authenticate_user(fake_db, username: str, password: str)

Autentica o usuário verificando o nome de usuário e a senha.

#### Parâmetros

- `fake_db` - O banco de dados fictício.
- `username: str` - O nome de usuário a ser autenticado.
- `password: str` - A senha do usuário a ser autenticada.

### create_access_token(data: dict, expires_delta: Optional[timedelta] = None)

Cria um token de acesso JWT.

#### Parâmetros

- `data: dict` - Dados a serem incorporados no token.
- `expires_delta: Optional[timedelta] = None` - O tempo de expiração do token.

### get_current_user(token: str = Depends(oauth2_scheme))

Obtém o usuário atual verificando o token de acesso.

#### Parâmetros

- `token: str = Depends(oauth2_scheme)` - O token de acesso a ser verificado.

### login_for_access_token(form_data: OAuth2PasswordRequestForm = Depends())

Autentica o usuário e retorna o token de acesso.

#### Parâmetros

- `form_data: OAuth2PasswordRequestForm = Depends()` - Os dados do formulário de login do usuário.

### read_users_me(current_user: User = Depends(get_current_user))

Retorna os detalhes do usuário autenticado.

#### Parâmetros

- `current_user: User = Depends(get_current_user)` - O usuário autenticado.

### read_secure_data(current_user: User = Depends(get_current_user))

Retorna uma mensagem de boas-vindas para o usuário autenticado.

#### Parâmetros

- `current_user: User = Depends(get_current_user)` - O usuário autenticado.

## Exemplo de uso

Para autenticar um usuário:

1. Faça uma solicitação POST para `/token` com o nome de usuário e a senha no corpo da solicitação.
2. Se a autenticação for bem-sucedida, você receberá um token de acesso.
3. Use este token de acesso como um cabeçalho de autorização Bearer nas solicitações subsequentes.

## Notas Importantes

- Este código é apenas um exemplo e não deve ser usado em produção. O SECRET_KEY deve ser mantido em segredo e não deve ser codificado no código.
- O banco de dados fictício é apenas para demonstração e deve ser substituído por um banco de dados real em uma aplicação de produção.