
# 1. Auswahl des Cloud-Anbieters
- Microsoft Azure, da die meisten Kenntnisse vorhanden 
- aufgrund der nativen Unterstützung für containerisierte Anwendungen
- verwaltete PostgreSQL-Datenbanken
- schnelle Bereitstellung produktionsreifer Dienste/Services möglich

# 2. Überblick über die Architektur
Dienst besteht aus drei Komponenten:
1. Backend-API – FastAPI-Anwendung, die in einem Container ausgeführt wird
2. Datenbank – Azure Database for PostgreSQL (managed)
3. Reverse-Proxy – Nginx, der eingehende HTTP-Anfragen verarbeitet und an das Backend weiterleitet

Der öffentliche Endpoint wird nur über Nginx verfügbar gemacht. Das Backend und die Datenbank sind privat und innerhalb eines virtuellen Netzwerks (VNet) isoliert.  

# 3. Compute Strategy
- Azure Container Apps wird für Container verwendet.
- Jeder Container läuft in seiner eigenen Umgebung mit isolierten Ressourcen.
- Container Apps bieten integrierte Skalierung, Zustandsüberwachung und Revisionskontrolle.

# 4. Networking Design
– Das Backend kommuniziert über ein privates VNet mit der Datenbank.
– Die Datenbank ist nicht öffentlich zugänglich.
- Nginx verarbeitet den eingehenden Datenverkehr und leitet Anfragen an das Backend weiter.

# 5. Secrets Management
- Azure Key Vault verwenden
- Container-Apps rufen Secrets zur Laufzeit über Umgebungsvariablen ab.
- Keine sensiblen Daten im Code oder im Repository speichern.
