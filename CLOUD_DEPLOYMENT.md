
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

