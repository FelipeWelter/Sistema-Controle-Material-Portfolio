# Sistema de Controle de Material · Portfólio

Aplicação Flask para inventário, disponibilidade e histórico de alterações por classe de material.

## Demonstração

O sistema reúne inventário, disponibilidade e acesso por classe de material. Neste cenário de demonstração, o recebimento de 30 unidades elevou o saldo do lote de 10 para 40.

### Inventário

![Listagem de rações com lote, validade e saldo de 40 unidades](docs/images/inventario.png)

### Histórico de alterações

O histórico registra a data, o usuário responsável, o motivo e os valores antes e depois da edição.

![Histórico do recebimento com quantidade anterior de 10 e nova quantidade de 40](docs/images/historico.png)

### Gestão de usuários

A tela administrativa permite consultar contas, perfis, classes atribuídas e situação de acesso. A captura mostra a conta fictícia **Admin Demo**.

![Tela de usuários com a conta de demonstração](docs/images/usuarios.png)

### Classe VII

Consulta de materiais com busca e contadores por situação. A captura mostra a lista inicial da demonstração.

![Menu da Classe VII com busca e contadores de disponibilidade](docs/images/classe-vii.png)

### Classe IX

Painel de viaturas com busca e indicadores de disponibilidade. A captura mostra a lista inicial da demonstração.

![Menu da Classe IX com busca e indicadores de disponibilidade](docs/images/classe-ix.png)

## Como rodar

```sh
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
export SECRET_KEY="$(openssl rand -hex 32)"
flask --app wsgi:app db upgrade
flask --app wsgi:app run --host 0.0.0.0 --port 5000
```

Com o banco migrado, rode `flask --app wsgi:app shell` e execute `from getpass import getpass; from app.models import db, User; u = User(full_name="Admin Demo", username="demo", role="admin", active=True); u.set_password(getpass()); db.session.add(u); db.session.commit()` para criar a conta local de demonstração. Defina `SECRET_KEY` no ambiente para manter as sessões entre reinícios.

No Codespaces, abra a porta **5000** pela aba **Portas**, com visibilidade **Privada**. Use a conta `demo` e a senha que você definiu.
