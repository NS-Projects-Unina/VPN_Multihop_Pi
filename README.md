# VPN_Multihop_Pi
Una VPN multi hop, utilizzando una raspberry pi e 2 droplet su DigitalOcean

Lo scopo del progetto è utilizzare un tunnel VPN Multi-Hop in uscita dal mio Raspberry, in parallelo ad un tunnel in entrata sullo stesso.

#MultiHop
Per la realizzazione del tunnel Multi-Hop è stato utilizzato un Raspberry Pi 5, una droplet situata a Francoforte e una droplet situata a NewYork (queste ultime acquistate tramite DigitalOcean). L'idea è quella di far convergere tutti i pacchetti che partono dal Raspberry in un tunnel multi-hop, seguendo il percorso Raspberry --> Francoforte --> NY. 
