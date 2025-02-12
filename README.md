# VPN_Multihop_Pi
Una VPN multi hop, utilizzando una raspberry pi e 2 droplet su DigitalOcean

Lo scopo del progetto è utilizzare un tunnel VPN Multi-Hop in uscita dal mio Raspberry, in parallelo ad un tunnel in entrata sullo stesso.

#MultiHop
Per la realizzazione del tunnel Multi-Hop tramite WireGuard è stato utilizzato un Raspberry Pi 5, una droplet situata a Francoforte, una droplet situata a NewYork (queste ultime acquistate tramite DigitalOcean). L'idea è quella di far convergere tutti i pacchetti che partono dal Raspberry in un tunnel multi-hop, seguendo il percorso Raspberry --> Francoforte --> NY. 
Sull'istanza di Francoforte, il tunnel verso NewYork è stato configurato in modo tale da riattivare automaticamente il single tunnel tra Raspberry e Francoforte al momento dello spegnimento, riducendo il bisogno degli interventi manuali sulle configurazioni. In questo modo, in base alle esigenze e al piacere dell'utilizzatore, il tunnel in uscita dal Raspberry sarà in modalità single-hop (Raspberry-->Francoforte, uscendo con l'IP pubblico di Francoforte) oppure in modalità multi-hop (Raspberry-->Francoforte-->NewYork, uscendo con l'IP pubblico di NewYork). Altri peer nelle configurazioni dei tunnel wireguard servono per utilizzare la VPN anche su dispositivi personali.

#VPN in ingresso
In parallelo ad un tunnel Multi-Hop in uscite, è stato realizzato anche un tunnel in ingresso, in modo tale da poter uscire su internet con l'indirizzo IP della mia abitazione anche se connessi ad una rete esterna. Per evitare problemi nel caso cambiasse l'IP pubblico a disposizione, si è fatto utilizzo di DuckDNS e di uno script che aggiorna ogni 5 minuti l'indirizzo IP corretto dell'interfaccia pubblica del Raspberry. Per accedere alla rete privata dall'esterno, è stato abilitato il port forwarding dal modem principale verso il Raspberry sulla porta 51825, ovvero quella scelta nel file di configurazione del tunnel WireGuard. Inoltre, è stato utilizzato il marking dei pacchetti per separare questo tunnel dal Multi-Hop in uscita. Infine, per gestire tutte le configurazioni anche a distanza e avere accesso al Raspberry tramite ssh una volta attivata la VPN, è stata abilitata la comunicazione tcp sulla porta 22.

In base a queste configurazioni, è possibile in qualsiasi momento e in qualsiasi luogo accedere a tutte le configurazioni create e modificarle in base alle proprie esigenze.
