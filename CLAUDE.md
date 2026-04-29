# CLAUDE.md

## Projekt

Rola Ansible `certificates` — zarządzanie certyfikatami CA i TLS (Vault PKI) w infrastrukturze rachuna-net.pl.

## Szybki start

```bash
# Lint roli
ansible-lint tasks/main.yml

# Sprawdzenie składni
ansible-playbook --syntax-check tests/test.yml
```

## Konwencje kodu

- **FQCN**: Zawsze używaj pełnych nazw modułów (`ansible.builtin.*`)
- **Prefiksy zmiennych**: `in_` dla zmiennych wejściowych roli, `_cert_` dla wewnętrznych
- **Bezpieczeństwo**: `no_log: true` na zadaniach z certyfikatami/kluczami
- **Uprawnienia plików**: klucze prywatne `0600`, katalogi kluczy `0750`, certyfikaty `0644`
- **Platformy**: Debian, Ubuntu, Alpine, RHEL/CentOS — różnice obsługiwane przez fakty `_cert_ca_*`
- **Min. Ansible**: 2.14

## Struktura

```
defaults/main.yml    — domyślne wartości zmiennych (in_certificates_vault_addr, in_certificates, in_certificates_bundle_paths, in_tls_certificates)
meta/main.yml        — metadane Ansible Galaxy
tasks/main.yml       — główna logika roli (CA + TLS)
```

## Język

- Dokumentacja: polski
- Kod i zmienne: angielski
- Commity: Conventional Commits (`feat`, `fix`, `docs`, `chore`, `refactor`, `ci`)

## Częste operacje

- Dodanie nowej platformy: zaktualizuj `_cert_ca_path`, `_cert_ca_update_cmd`, `_cert_ca_extension` w `tasks/main.yml` oraz `meta/main.yml`
- Dodanie nowego typu wyjścia (np. PKCS12): dodaj nowe zadania po wzorcu istniejących (create dir + save file)
