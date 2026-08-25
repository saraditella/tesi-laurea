# Ingegnerizzazione di un sistema CRM a microservizi: Integrazione, Automazione dei processi e Business Intelligence

**Candidata:** Sara Di Tella (Matricola: 0512120582)  
**Corso di Laurea:** Laurea Triennale in Informatica  
**Università:** Università degli Studi di Salerno — Dipartimento di Informatica  
**Relatore:** Prof. Fabio Palomba  
**Tutor Aziendale:** Christian Vitale (Large Systems)  
**Anno Accademico:** 2025-2026  

---

## Tesi Completa
* **[Scarica la Tesi di Laurea (PDF)](./tesi-sara-di-tella.pdf)**

---

## Abstract

Questo lavoro di tesi documenta l'esperienza di tirocinio curriculare svolta in azienda, dedicata al progettare e implementare una piattaforma CRM a microservizi. Il progetto è nato per superare la frammentazione dei dati commerciali, finora gestiti tramite strumenti isolati e non comunicanti tra loro, che rendeva difficile ricostruire lo stato delle trattative in corso. La soluzione adottata è una piattaforma centralizzata in grado di preservare la riservatezza dei dati aziendali. Il sistema automatizza i flussi di vendita e genera analisi e statistiche aggiornate sullo stato della pipeline commerciale.

L'intervento si è diviso in due fasi distinte. Inizialmente si è lavorato al refactoring dei tre microservizi già presenti in azienda: *Personal Data* (uniformazione delle anagrafiche), *Notification* (automazione dell'invio delle notifiche) e *File Manager* (centralizzazione della gestione degli allegati). Nella seconda fase sono stati sviluppati da zero i due moduli centrali dell'architettura. Il *Configurator* è un motore di orchestrazione con vista Kanban per gestire l'intero ciclo di vita delle trattative commerciali e registrarne lo storico tramite Audit Log. Il modulo *Stats*, dedicato alla Business Intelligence, elabora invece metriche di vendita quali il tasso di successo delle opportunità (Win Rate), le motivazioni di perdita dei contratti e i tempi medi di stazionamento nelle singole fasi della pipeline.

L'architettura si basa su Java e sul framework Spring Boot. Le comunicazioni via rete tra i singoli servizi sono affidate a Spring Cloud OpenFeign, mentre la persistenza dei dati si basa su PostgreSQL. L'uso combinato di Spring Data JPA e delle Criteria API ha permesso di costruire query con filtri opzionali e composizione dinamica delle condizioni, non ottenibile con query JPQL statiche. La sicurezza degli endpoint è gestita tramite token JWT stateless e un modello di controllo degli accessi basato sui ruoli (RBAC), con il token propagato alle chiamate inter-servizio tramite gli interceptor di Feign.

L'isolamento dei microservizi garantisce la continuità delle operazioni principali: un eventuale malfunzionamento del modulo Stats o del servizio Notification, ad esempio, non compromette la gestione delle trattative su Configurator. L'aver disaccoppiato i servizi semplifica l'integrazione delle funzionalità future, già previste per la gestione della fatturazione e il monitoraggio dei flussi di cassa.

---

## Stack Tecnologico
* **Linguaggio & Framework:** Java 21, Spring Boot 3.x, Spring Cloud OpenFeign, Spring Data JPA
* **Database & Migrazioni:** PostgreSQL, Flyway, Hibernate
* **Mappatura & Architettura:** MapStruct, RESTful APIs, JWT, Role-Based Access Control (RBAC)
* **DevOps & Containerizzazione:** Docker
