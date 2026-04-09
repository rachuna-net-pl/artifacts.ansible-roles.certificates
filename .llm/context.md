# Kontekst projektu

## Cel

Rola Ansible `certificates` zarządza certyfikatami w infrastrukturze rachuna-net.pl. Obsługuje dwa scenariusze:

1. **Certyfikaty CA** — pobieranie certyfikatów CA z URL i instalacja w systemowym magazynie zaufanych certyfikatów
2. **Certyfikaty TLS** — wydawanie certyfikatów TLS przez HashiCorp Vault PKI API

## Architektura

- Vault PKI jest centralnym źródłem certyfikatów TLS
- Token Vault przekazywany przez zmienną środowiskową `VAULT_TOKEN`
- Rola obsługuje wiele platform (Debian, Ubuntu, Alpine, RHEL) z automatycznym wykrywaniem ścieżek

## Zależności

- HashiCorp Vault z silnikiem PKI
- Dostęp sieciowy do Vault z zarządzanych hostów (lub z hosta wykonującego playbook)
- Brak zależności od innych ról Ansible

## Struktura plików

```
certificates/
├── defaults/main.yml    # Domyślne wartości zmiennych
├── meta/main.yml        # Metadane Galaxy
├── tasks/main.yml       # Główna logika roli
├── docs/                # Obrazki do dokumentacji
├── .llm/                # Kontekst dla LLM
├── README.md            # Dokumentacja
├── LICENSE              # Licencja (niekomercyjna)
├── CONTRIBUTING.md      # Przewodnik dla kontrybutorów
└── CODE_OF_CONDUCT.md   # Kodeks postępowania
```
