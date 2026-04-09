# Konwencje projektu

## Ansible

- Używaj FQCN (Fully Qualified Collection Name) dla wszystkich modułów, np. `ansible.builtin.copy`
- Minimalna wersja Ansible: 2.14
- Nazwy zmiennych roli z prefiksem `in_` (input), np. `in_certificates`, `in_tls_certificates`
- Zmienne wewnętrzne roli z prefiksem `_cert_`, np. `_cert_ca_path`
- `no_log: true` dla wszystkich zadań operujących na certyfikatach i kluczach
- Klucze prywatne: uprawnienia `0600`, katalogi `0750`
- Certyfikaty publiczne: uprawnienia `0644`
- Warunki `when` w formie listy YAML dla wielu warunków
- Używaj `loop_control.label` aby ograniczyć wyjście w logach

## Obsługiwane platformy

- Debian (bullseye, bookworm)
- Ubuntu (focal, jammy, noble)
- Alpine (all)
- RHEL/CentOS (8, 9)

Różnice międzyplatformowe obsługiwane przez zmienne faktów (`_cert_ca_path`, `_cert_ca_update_cmd`, `_cert_ca_extension`).

## Język

- Dokumentacja w języku polskim
- Nazwy zmiennych i kodu w języku angielskim
- Komentarze w kodzie po angielsku

## Git

- Konwencja commitów: Conventional Commits
- Typy: `feat`, `fix`, `docs`, `chore`, `refactor`, `ci`
