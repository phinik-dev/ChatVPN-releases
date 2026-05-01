# ChatVPN for Linux — v2.8.2

ChatVPN — VPN-клиент с поддержкой современных VPN протоколов.

| | |
|---|---|
| Текущая версия | **2.8.2** |
| Архитектуры    | x86_64 (amd64), aarch64 (arm64) |
| GPG-ключ       | `CA2A478FE9E7E4EA` |

---

## Установка через официальный репозиторий (рекомендуется)

Подключив репозиторий один раз, дальше получаете обновления стандартной командой `apt upgrade` / `dnf upgrade`.

### Debian / Ubuntu / Mint / Pop!_OS

```bash
sudo install -d -m 0755 /etc/apt/keyrings
curl -fsSL https://phinik-dev.github.io/ChatVPN-releases/chatvpn.gpg \
  | sudo gpg --dearmor -o /etc/apt/keyrings/chatvpn.gpg
echo "deb [signed-by=/etc/apt/keyrings/chatvpn.gpg] https://phinik-dev.github.io/ChatVPN-releases/apt stable main" \
  | sudo tee /etc/apt/sources.list.d/chatvpn.list
sudo apt update
sudo apt install chatvpn
```

### Fedora / RHEL / Rocky / Alma / openSUSE

```bash
sudo curl -fsSL https://phinik-dev.github.io/ChatVPN-releases/rpm/chatvpn.repo \
  -o /etc/yum.repos.d/chatvpn.repo
sudo dnf install chatvpn          # или: sudo zypper install chatvpn
```

При первой установке dnf/zypper попросит подтвердить импорт GPG-ключа с
fingerprint `209334197FCDB901B1E1365CCA2A478FE9E7E4EA` — соглашайтесь.

---

## Прямое скачивание `.deb` / `.rpm` / `.tar.gz`

Если репозиторий по каким-то причинам недоступен — все пакеты этого релиза
лежат прямо в [GitHub Release v2.8.2](../../releases/tag/v2.8.2):

| Файл | Для чего |
|---|---|
| `chatvpn_2.8.2_amd64.deb` | Debian/Ubuntu, 64-bit ПК |
| `chatvpn_2.8.2_arm64.deb` | Debian/Ubuntu, ARM (Pi и т.д.) |
| `chatvpn-2.8.2-1.x86_64.rpm` | Fedora/RHEL/openSUSE, 64-bit ПК |
| `chatvpn-2.8.2-1.aarch64.rpm` | Fedora/RHEL, ARM |
| `chatvpn-2.8.2-linux-amd64.tar.gz` | Arch, Steam Deck, Alpine, всё прочее |
| `chatvpn-2.8.2-linux-arm64.tar.gz` | то же, ARM |

```bash
# .deb
sudo apt install ./chatvpn_2.8.2_amd64.deb

# .rpm
sudo dnf install ./chatvpn-2.8.2-1.x86_64.rpm

# .tar.gz
tar xzf chatvpn-2.8.2-linux-amd64.tar.gz
cd chatvpn-2.8.2-linux-amd64 && sudo ./install.sh
```

---

## Особые случаи

- **Bazzite / Fedora Silverblue / Kinoite / Bluefin** — используйте `rpm-ostree install` со скачанным `.rpm`-файлом и перезагружайтесь:
  ```bash
  sudo rpm-ostree install ./chatvpn-2.8.2-1.x86_64.rpm
  sudo systemctl reboot
  ```
- **Steam Deck (SteamOS)** — переключитесь в Desktop Mode, выполните `sudo steamos-readonly disable`, затем `.tar.gz`-вариант с `install.sh`.

---

## Проверка подписи

Все пакеты подписаны GPG-ключом ChatVPN с fingerprint:

```
209334197FCDB901B1E1365CCA2A478FE9E7E4EA
```

Публичный ключ — [https://phinik-dev.github.io/ChatVPN-releases/chatvpn.gpg](https://phinik-dev.github.io/ChatVPN-releases/chatvpn.gpg). При установке через `apt`/`dnf` подпись проверяется автоматически.
