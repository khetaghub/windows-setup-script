# Setup Script (winget + PowerShell)

## Описание

Скрипт `install-apps.ps1` автоматически устанавливает приложения через `winget`.

Цели:

- убрать ручную установку софта
- ускорить настройку нового ПК
- сделать процесс воспроизводимым

---

## Что будет установлено

| Приложение | Winget ID | Версия |
|---|---:|---:|
| Bitwarden | `Bitwarden.Bitwarden` | `2026.3.1` |
| CapCut | `ByteDance.CapCut` | `8.5.0.3590` |
| Chocolatey | `Chocolatey.Chocolatey` | `2.7.1.0` |
| Discord | `Discord.Discord` | latest |
| Epic Games Launcher | `EpicGames.EpicGamesLauncher` | `1.3.161.0` |
| Git | `Git.Git` | `2.54.0` |
| Notepad++ | `Notepad++.Notepad++` | `8.9.2` |
| Notion | `Notion.Notion` | `7.9.0` |
| Postman | `Postman.Postman` | `12.7.6` |
| qBittorrent | `qBittorrent.qBittorrent` | `5.1.4` |
| Steam | `Valve.Steam` | `2.10.91.91` |
| Telegram Desktop | `Telegram.TelegramDesktop` | `6.7.8` |
| Yandex Browser | `Yandex.Browser` | `25.8.5.948` |

---

## Требования

- Windows 10 / 11;
- установлен `winget` / App Installer;
- запуск от имени администратора, так как часть пакетов устанавливается с `--scope machine`.

---

## Структура файлов

```text
install-apps.ps1   # основной PowerShell-скрипт установки
install.bat        # обёртка для запуска PowerShell-скрипта
```

---

## Запуск

### Через `install.bat`

Запустить `install.bat` от имени администратора.

### Через PowerShell

```powershell
powershell -ExecutionPolicy Bypass -File .\install-apps.ps1
```

---

## Поведение скрипта

Перед установкой скрипт:

1. проверяет, что он запущен от имени администратора
2. проверяет наличие `winget`
3. для каждого приложения проверяет, установлено ли оно уже
4. если приложение найдено, пропускает установку
5. если приложение не найдено, устанавливает его через `winget install`
