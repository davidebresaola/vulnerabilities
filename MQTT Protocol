
# Protocollo MQTT

## Descrizione del Protocollo MQTT

MQTT (Message Queuing Telemetry Transport) è un protocollo di messaggistica leggero progettato per connessioni a bassa larghezza di banda e reti con elevata latenza o intermittenza. È particolarmente utilizzato in applicazioni IoT (Internet of Things) dove dispositivi con risorse limitate necessitano di comunicare in modo efficiente.

### Principi Fondamentali del Protocollo MQTT:

1. **Architettura Pub/Sub**:
   - **Publisher**: Invia messaggi su determinati argomenti (topics).
   - **Broker**: Intermediario che riceve messaggi dai publisher e li inoltra ai subscriber.
   - **Subscriber**: Si iscrive a specifici argomenti per ricevere i messaggi corrispondenti.

2. **Argomenti (Topics)**:
   - Struttura gerarchica per la categorizzazione dei messaggi, ad esempio `sensori/temperatura/casa`.
   - I subscriber si iscrivono a uno o più argomenti di interesse.

3. **Qualità del Servizio (QoS)**:
   - **QoS 0**: "At most once" - Il messaggio è consegnato una sola volta, senza garanzia di arrivo.
   - **QoS 1**: "At least once" - Il messaggio è consegnato almeno una volta, con possibile duplicazione.
   - **QoS 2**: "Exactly once" - Il messaggio è consegnato esattamente una volta, garantendo la consegna senza duplicati.

4. **Ritenzione dei Messaggi (Retained Messages)**:
   - Un messaggio ritenuto viene conservato dal broker e inviato immediatamente a ogni nuovo subscriber dell'argomento pertinente.

5. **Durata delle Sessioni**:
   - **Sessioni Persistenti**: Conservano le informazioni di sottoscrizione e i messaggi non consegnati durante le disconnessioni temporanee.
   - **Sessioni Non Persistenti**: Le informazioni di sottoscrizione e i messaggi non consegnati vengono scartati alla disconnessione.

6. **Keep-Alive e PINGREQ**:
   - Il client invia periodicamente messaggi PINGREQ per mantenere aperta la connessione con il broker.
   - Se il broker non riceve il keep-alive entro un certo intervallo, chiude la connessione.

7. **Autenticazione e Sicurezza**:
   - Supporta autenticazione tramite username e password.
   - Può utilizzare SSL/TLS per cifrare la connessione e garantire la sicurezza dei dati trasmessi.

### Funzionamento di Base:

1. **Connessione**: Il client si connette al broker specificando l'ID del client e le opzioni di connessione come keep-alive e clean session.
2. **Sottoscrizione**: Il client si iscrive a uno o più argomenti per ricevere i messaggi.
3. **Pubblicazione**: Il client pubblica messaggi su argomenti specifici. Il broker distribuisce questi messaggi a tutti i subscriber pertinenti.
4. **Disconnessione**: Il client può disconnettersi in modo pulito dal broker inviando un messaggio DISCONNECT.

### Vantaggi di MQTT:

- **Leggerezza**: Bassa overhead di rete e semplice implementazione, ideale per dispositivi con risorse limitate.
- **Efficienza**: Ottimizzato per reti con latenza elevata e connessioni intermittenti.
- **Scalabilità**: Supporta un gran numero di client con configurazioni di argomenti flessibili.

### Svantaggi di MQTT:

- **Sicurezza**: Richiede configurazione e gestione per garantire sicurezza, come l'uso di SSL/TLS.
- **Qualità del Servizio**: Le garanzie di consegna dipendono dal livello di QoS configurato, e i livelli superiori possono introdurre overhead.

In sintesi, MQTT è un protocollo di messaggistica molto utilizzato nelle applicazioni IoT grazie alla sua leggerezza, efficienza e flessibilità nella gestione delle comunicazioni tra dispositivi.

---

## Vulnerabilità del Protocollo MQTT

Il protocollo MQTT, pur essendo molto utile e versatile per le applicazioni IoT, presenta alcune vulnerabilità che devono essere considerate e mitigate per garantire la sicurezza delle comunicazioni. Ecco le principali vulnerabilità:

### 1. **Autenticazione Debole**
- **Problema**: MQTT supporta l'autenticazione basata su username e password, ma non fornisce meccanismi avanzati di autenticazione di default.
- **Mitigazione**: Implementare autenticazione a due fattori (2FA) o utilizzare certificati client per autenticazione robusta.

### 2. **Assenza di Crittografia**
- **Problema**: I messaggi MQTT possono essere trasmessi in chiaro, rendendoli vulnerabili agli attacchi di intercettazione (eavesdropping).
- **Mitigazione**: Utilizzare SSL/TLS per cifrare la comunicazione tra client e broker.

### 3. **Man in the Middle (MitM)**
- **Problema**: Senza crittografia, un attaccante può intercettare e modificare i messaggi tra client e broker.
- **Mitigazione**: Utilizzare certificati SSL/TLS per autenticare sia il client che il broker e garantire l'integrità dei messaggi.

### 4. **Autorizzazione Inadeguata**
- **Problema**: MQTT non fornisce controlli di accesso granulari per argomenti, permettendo a qualsiasi client con credenziali valide di pubblicare o sottoscrivere qualsiasi argomento.
- **Mitigazione**: Configurare politiche di autorizzazione rigorose nel broker per limitare l'accesso a specifici argomenti basato sui ruoli.

### 5. **Denial of Service (DoS)**
- **Problema**: Un attaccante può sovraccaricare il broker con connessioni o messaggi, portando a un’interruzione del servizio.
- **Mitigazione**: Implementare limiti di connessione, rate limiting, e meccanismi di rilevamento delle anomalie per identificare e bloccare attività sospette.

### 6. **Retention Messages Abusi**
- **Problema**: I messaggi trattenuti possono essere usati per inviare messaggi malevoli o per accumulare dati inutili che possono sovraccaricare il broker.
- **Mitigazione**: Limitare l'uso dei messaggi trattenuti e monitorare i messaggi trattenuti nel broker.

### 7. **Brute Force Attacks**
- **Problema**: Senza misure adeguate, un attaccante può tentare attacchi di forza bruta per indovinare username e password.
- **Mitigazione**: Implementare blocco degli account dopo un numero definito di tentativi falliti e utilizzare password robuste.

### 8. **Lack of Logging and Monitoring**
- **Problema**: La mancanza di logging e monitoring adeguati può rendere difficile rilevare e rispondere agli attacchi.
- **Mitigazione**: Configurare il broker per registrare e monitorare tutti gli eventi rilevanti, inclusi tentativi di connessione, messaggi pubblicati e errori.

### 9. **Topic Injection**
- **Problema**: Un attaccante potrebbe iniettare messaggi in argomenti non autorizzati per influenzare il comportamento dei dispositivi subscriber.
- **Mitigazione**: Implementare validazione dei messaggi e controlli di accesso rigorosi per ogni argomento.

### 10. **Versione del Protocollo**
- **Problema**: Utilizzare versioni non aggiornate del protocollo può esporre a vulnerabilità note.
- **Mitigazione**: Assicurarsi di utilizzare la versione più recente del protocollo MQTT e applicare regolarmente patch di sicurezza.


# Vulnerabilità Infami in MQTT

## CVE-2023–28366: Perdita di Memoria Remota con Messaggi QoS 2
Il broker in Eclipse Mosquitto dalla versione 1.3.2 alla 2.x prima della 2.0.16 ha una perdita di memoria che può essere sfruttata da remoto quando un client invia molti messaggi QoS 2 con ID messaggio duplicati e non risponde ai comandi PUBREC. Questo si verifica a causa della gestione errata di EAGAIN dalla funzione send di libc.

## CVE-2017–7650: Configurazione Predefinita Insicura
Una delle vulnerabilità comuni nelle implementazioni MQTT è l'uso di configurazioni predefinite insicure. Alcuni broker MQTT vengono forniti con impostazioni predefinite che privilegiano la facilità di configurazione rispetto alla sicurezza, rendendoli vulnerabili agli attacchi. Gli attaccanti possono sfruttare queste impostazioni predefinite per ottenere accesso non autorizzato o eseguire azioni dannose.

## CVE-2023–5632: Consumo Eccessivo della CPU con Connessione Vuota
In Eclipse Mosquitto prima e inclusa la versione 2.0.5, stabilire una connessione al server mosquitto senza inviare dati causa l'aggiunta dell'evento EPOLLOUT, che risulta in un consumo eccessivo della CPU. Questo potrebbe essere utilizzato da un attore malintenzionato per eseguire un attacco di tipo denial of service. Questo problema è stato risolto nella versione 2.0.6.

## CVE-2021–34434: Problema di Revoca delle Sottoscrizioni
In Eclipse Mosquitto versioni dalla 2.0 alla 2.0.11, quando si utilizza il plugin di sicurezza dinamica, se la capacità di un client di effettuare sottoscrizioni a un argomento viene revocata mentre un client duraturo è offline, allora le sottoscrizioni esistenti per quel client non vengono revocate.

## CVE-2020–11976: Overflow del Buffer
Le vulnerabilità di overflow del buffer nelle implementazioni MQTT possono portare ad attacchi di esecuzione di codice remoto. La CVE-2020–11976 illustra scenari in cui gli attaccanti possono sfruttare difetti di overflow del buffer per iniettare ed eseguire codice dannoso su dispositivi o server che eseguono software MQTT vulnerabile.

## Migliori Pratiche per la Sicurezza MQTT:

### Implementare Autenticazione e Autorizzazione Sicura
Imporre meccanismi di autenticazione robusti come username/password o certificati client per verificare l'identità dei client MQTT. Inoltre, implementare politiche di controllo degli accessi granulari per limitare l'accesso dei client agli argomenti autorizzati.

### Abilitare la Crittografia
Utilizzare Transport Layer Security (TLS) per crittografare i dati scambiati sulle connessioni MQTT. Questo garantisce la riservatezza e l'integrità, prevenendo l'intercettazione non autorizzata o la manomissione dei messaggi MQTT.

### Aggiornare e Patchare Regolarmente
Rimanere vigili sugli aggiornamenti e le patch rilasciati dai fornitori di software MQTT. Aggiornare regolarmente i broker MQTT, i client e le librerie correlate per patchare le vulnerabilità note e rafforzare la sicurezza.

### Monitorare le Anomalie
Implementare sistemi di monitoraggio e rilevamento delle intrusioni per rilevare e rispondere alle attività sospette sulle reti MQTT. Monitorare i modelli di traffico insoliti, i tentativi di accesso non autorizzati o i potenziali attacchi DoS.

### Seguire le Pratiche di Codifica Sicura
Adottare pratiche di codifica sicura quando si sviluppano applicazioni MQTT o implementazioni personalizzate. Evitare insidie comuni come overflow del buffer, difetti di validazione degli input o configurazioni predefinite insicure.


### Conclusione
Per mitigare queste vulnerabilità, è essenziale implementare pratiche di sicurezza robuste, inclusa la crittografia, l'autenticazione e l'autorizzazione forti, oltre a un monitoraggio continuo e una gestione delle vulnerabilità. Questi passaggi aiutano a proteggere le implementazioni MQTT dalle minacce comuni e a garantire la sicurezza delle comunicazioni nelle applicazioni IoT.
