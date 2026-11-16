# Sistema de Controle de Material · Portfólio

Aplicação Flask para inventário, disponibilidade e histórico de alterações por classe de material.

```sh
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
flask --app wsgi:app db upgrade
flask --app wsgi:app run
```

Com o banco migrado, rode `flask --app wsgi:app shell` e execute `from getpass import getpass; from app.models import db, User; u = User(full_name="Admin Demo", username="demo", role="admin", active=True); u.set_password(getpass()); db.session.add(u); db.session.commit()` para criar a conta local de demonstração. Defina `SECRET_KEY` no ambiente para manter as sessões entre reinícios.
