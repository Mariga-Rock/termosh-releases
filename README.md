# Termosh

Android-клиент для **SSH** и **mosh**. Всё работает локально: без серверов,
без аккаунтов, без телеметрии. Пароли и ключи хранятся в Android Keystore и
SQLCipher.

**Статус:** бета

## Возможности

- **SSH** — пароль, публичный ключ (Ed25519 / RSA / ECDSA P-256), несколько ключей с fallback, ProxyJump.
- **mosh** — нативный клиент через JNI + настоящий PTY. Переживает смену сети и долгие паузы.
- **Вкладки** — несколько серверов одновременно, независимые индикаторы, split view.
- **Импорт:** `~/.ssh/config` (с `Include`), `known_hosts` (включая хешированные), ConnectBot XML, `.termosh` / `.termoshvault`.
- **Экспорт:** `.termosh` (без секретов / с секретами), `.termoshvault` (AES-GCM + PBKDF2), OpenSSH config.
- **Терминал** — InstantInput (строка по Enter целиком), KeyboardBar (Ctrl/Alt/Esc/стрелки), кнопки «вставить из буфера» и «копировать вывод» рядом с Send, double-tap вставка, long-press выделение.
- **Сниппеты.**
- **Три темы:** Tokyo Night, Catppuccin Frappe, GitHub Light.
- **Безопасность** — Android Keystore (TEE/StrongBox) → AES-256-GCM → SQLCipher. PBKDF2-HMAC-SHA256 (100k) для `.termoshvault`. Ed25519-подписи лицензий.

## Установка

1. Открой [последний релиз](https://github.com/Mariga-Rock/termosh-releases/releases).
2. Скачай `app-release.apk` на телефон.
3. Android скажет «Установка заблокирована» → Настройки → разреши установку из этого источника.
4. Вернись, установи APK.
5. Открой Termosh, добавь сервер, подключись.

## Требования

- Android 14 или новее (minSdk = targetSdk = 34).
- Процессор `arm64-v8a` (все современные телефоны).

## Что работает / что не работает

**Работает:** SSH, mosh, вкладки, split view, импорт/экспорт, сниппеты, темы, лицензирование.

**Не проверено:** ProxyJump, внешняя (физическая) клавиатура, `Include` в OpenSSH config на разных версиях Android.

## Планы развития

**Скрыто до стабилизации:** TOTP-хранилище, SFTP, port forwarding, переменные окружения сервера, сортировка списка серверов.

**Не реализовано:** автоподстановка TOTP при SSH-входе, tmux-панель, rename/drag-and-drop вкладок, пинч-зум, Termius-импорт.

## Обратная связь

- **Баг-репорт:** открой [issue](https://github.com/Mariga-Rock/termosh/issues). Опиши шаги воспроизведения, версию Android, модель телефона.
- **Логи падения:** приложи crash.log (если есть)
- **Поддержка (тг)** [@termosh_app_bot](https://t.me/termosh_app_bot)

## Благодарности

- [sshj](https://github.com/hierynomus/sshj)
- [mosh](https://mosh.org/)
- [BouncyCastle](https://www.bouncycastle.org/)
- [SQLCipher](https://www.zetetic.net/sqlcipher/)
- [Catppuccin](https://catppuccin.com/)

## Лицензия

Исходный код не распространяется.
