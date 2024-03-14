# netbox_translation

Включить русский перевод в файле `netbox/netbox/settings.py`:

```python
LANGUAGE_CODE = 'ru-ru'
ENABLE_LOCALIZATION = True
```

Пути для замены иконок и лого:

```
netbox/static/netbox.ico
netbox/static/netbox_icon.svg
netbox/static/netbox_logo.png
netbox/static/netbox_logo.svg
```

Если нужно изменить порядок меню:

```
netbox/netbox/navigation/menu.py
```

Фикс отобраения плагинов и привелегий для них в файле `netbox/utilities/templatetags/navigation.py` заменить строку:

```python
if not user.has_perms(item.permissions):
```

на 

```python
if not user.has_perms([_.replace('plugins:', '') for _ in item.permissions]):
```

## Если не нравится комюнити перевод
Скомпилировать словарь:

```bash
msgfmt django.po -o django.mo;
```

Поместить словари в русскую локализацию:

```
netbox/translations/ru/LC_MESSAGES/django.po
netbox/translations/ru/LC_MESSAGES/django.mo
```
