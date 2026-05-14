# Babloo Kumar – Portfolio (Django)

## Local Setup

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Visit: http://127.0.0.1:8000

Admin panel: http://127.0.0.1:8000/admin

---

## Deploy on Railway (Free)

1. Push project to GitHub
2. Go to https://railway.app → New Project → Deploy from GitHub
3. Add environment variables:
   - `SECRET_KEY` = your-secret-key
   - `DEBUG` = False
   - `ALLOWED_HOSTS` = your-app.railway.app
4. Railway auto-detects Django and deploys

---

## Deploy on Render (Free)

1. Push to GitHub
2. Go to https://render.com → New Web Service
3. Build Command: `pip install -r requirements.txt && python manage.py migrate`
4. Start Command: `gunicorn portfolio.wsgi`
5. Add env vars: `SECRET_KEY`, `DEBUG=False`, `ALLOWED_HOSTS`

---

## Deploy on PythonAnywhere (Free)

1. Upload project files
2. Create virtualenv, install requirements
3. Set WSGI file to point to `portfolio.wsgi`
4. Run `python manage.py migrate` in console
5. Set `ALLOWED_HOSTS = ['yourusername.pythonanywhere.com']`

---

## Production Checklist

- Set `DEBUG = False`
- Set a strong `SECRET_KEY`
- Add `whitenoise` for static files (already in requirements)
- Add to settings.py:
  ```python
  MIDDLEWARE = [
      'whitenoise.middleware.WhiteNoiseMiddleware',
      ...
  ]
  STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'
  ```
- Run `python manage.py collectstatic`

---

## Contact Form

All messages from the contact form are saved in the database.
View them at `/admin` → Contact Messages.
