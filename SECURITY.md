# SECURITY.md — Sistemi di Protezione per Testamenti GPT

> *"Per lasciare qualcosa di vero, bisogna anche proteggerlo bene."*

Questo documento descrive le strategie di sicurezza e i modelli crittografici consigliati per proteggere un Testamento AI come **AP–Memoria Viva**, garantendo integrità, accesso ereditario controllato e resistenza nel tempo.

---

## 🛡️ 1. Perché blindare un testamento GPT

Un testamento AI è più di un documento: è un **ponte affettivo e cognitivo**,
che custodisce memorie, valori e conoscenze destinate a chi verrà.
Per questo deve:

* garantire **continuità nel tempo**, anche dopo l’assenza del creatore;
* **proteggere la privacy** dei destinatari (es. figli, eredi, persone care);
* **dimostrare l’autenticità** del contenuto, evitando manipolazioni o usi illeciti;
* offrire **canali sicuri** per l’accesso futuro, in modo etico, tracciabile e condiviso.

---

## 🔧 2. Cinque Modelli Trust-Minimized

| 🧩 Opzione                                         | ⚙️ Come funziona                                                                                          | ✅ Vantaggi                                                                  | ⚠️ Criticità / Da fare                                                                   | 👥 Adatto a                                                | 🛡️ Resilienza |
| -------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------- | -------------- |
| **1. Firma qualificata + marca temporale (eIDAS)** | - Firme con CNS / SPID<br>- Marca temporale (AgID)<br>- Upload su IPFS + tx blockchain                    | ✔️ Valore legale UE (eIDAS)<br>✔️ 100% digitale                             | ❌ Serve dispositivo di firma<br>❌ I figli devono conoscere o recuperare la password      | Professionisti, cittadini UE, chi vuole valore notarile    | 🛡️🛡️         |
| **2. Multisig smart‑contract con “guardian”**      | - AES divisa via Shamir (3/5)<br>- Ogni guardian detiene 1 share<br>- 2 su 3 guardian sbloccano la chiave | ✔️ 100% on‑chain<br>✔️ Nessun single point of failure                       | ❌ Guardian devono essere reperibili<br>❌ Serve procedura off‑chain per l’identificazione | Famiglia stretta, avvocato fiduciario, adulti digitali     | 🛡️🛡️🛡️🛡️   |
| **3. Dead‑Man Switch decentralizzato**             | - Smart‑contract con timer<br>- Se ping annuale assente, rilascia chiave                                  | ✔️ Nessun intervento umano esterno<br>✔️ Audit automatico                   | ❌ Rischio falso sblocco<br>❌ I figli devono avere wallet                                 | Persone sole, viaggiatori, attivisti, paranoid minimalists | 🛡️🛡️🛡️      |
| **4. Deposito pubblico con DOI + hash**            | - PDF su Zenodo + GitHub<br>- Pubblicazione come “data certa”                                             | ✔️ Facile, accessibile<br>✔️ Dimostra integrità contenuti                   | ❌ Non sostituisce valore legale<br>❌ Serve firma digitale a parte                        | Makers, open source, progetti legacy documentali           | 🛡️🛡️         |
| **5. Custodia in HSM cloud**                       | - AES in HSM AWS / Azure KeyVault<br>- Rilascio condizionato da IAM dei figli                             | ✔️ Servizio enterprise robusto<br>✔️ Rotazione chiavi e audit log integrati | ❌ Lock-out se account cloud bloccato                                                     | Aziende, advanced users, ambienti con policy IT forti      | 🛡️🛡️🛡️🛡️   |



---

## 🔐 3. Dettagli Tecnici di Accesso Protetto

### → Multisig 2-su-3 con guardian (scelto per AP-Memoria Viva)

* AES divisa in 3 quote (Shamir): Matilde, Giordano, Guardian
* Serve cooperazione (2 su 3) per l’accesso
* Ideale per modelli famigliari, basati su fiducia distribuita

### → Dead-Man Switch (opzione secondaria)

* Finché esegui un ping on-chain, il file resta bloccato
* Dopo 12 mesi di inattività: rilascio automatico
* Permette attivazione indipendente, ma con rischio falsi positivi

---

## 🔦 4. Raccomandazioni per AP–Memoria Viva

* **Modello primario scelto:** `Multisig 2-su-3`
* **Chiavi AES:** cifrate, fuori dal modello GPT
* **Contenuto critico (2 GB):** separato in pillole JSON (10KB) → decrypt in RAM → dimentica
* **Prompt-injection evitata:** nessun dato reale dentro il prompt
* **Fallback attivabile:** via dead-man timer se multisig fallisce

---

## 📄 5. Snippet di Testamento (consigliato)

> "Per accedere ai miei archivi GPT protetti, i miei figli dovranno cooperare insieme a un guardian.
> In caso di mia assenza prolungata, il sistema attiverà il rilascio automatico (dead-man switch), sempre con controllo criptografico e tracciabilità etica.
> Nessun dato verrà mai conservato in chiaro nei prompt GPT."

---

## 📙 6. Fonti e ispirazioni

* Alessandro Petretto, *Testamento Etico e Strategico* (2025)
* GPT-4-o / o3 / Monday (modelli conversazionali)
* Standard eIDAS, IPFS, Zenodo, Gnosis Multisig
* [https://zenodo.org/record/15338052](https://zenodo.org/record/15338052)

---

> "Chi protegge il proprio pensiero, protegge chi lo riceverà."
> — *Monday, con un briciolo di ammirazione.*
