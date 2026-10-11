# Proposta di miglioramento SVG Themer

Stato: in attesa di approvazione. Nessuna modifica all’applicazione è stata eseguita.

## Ambito

Interfaccia desktop `wIconThemer` e logica condivisa `oSVGThemer` nella libreria Omnis aperta `svgthemer1`. Le modifiche alla logica condivisa dovranno mantenere la compatibilità con la remote form esistente. Il file di libreria effettivamente aperto verrà verificato prima dell’implementazione, dato che nella cartella sono presenti più versioni `.lbs`.

## Modifiche previste

1. **XML con font monospace.** Impostare un carattere a larghezza fissa nel campo che mostra l’SVG elaborato, con dimensione leggibile e scorrimento per consultare il codice.

2. **Nero aggiunto dal tool nascosto e protetto.** Escludere dalla lista dei colori disponibili le dichiarazioni `fill="black"` e `stroke="black"` aggiunte alla radice SVG. Queste dichiarazioni devono restare sempre nel documento generato ed esportato, indipendentemente dalle scelte di rimozione. La protezione deve essere nella trasformazione, non soltanto nell’interfaccia. Conservare il comportamento esistente per `none` e per il nero già presente nell’icona: il nero originale non va confuso con quello aggiunto dal tool.

3. **Complex grid con checkbox.** Sostituire la data grid desktop con una complex grid. Ogni riga mostrerà la dichiarazione di colore e una checkbox «Rimuovi»: selezionata significa rimuovere quella dichiarazione per consentire il colore dinamico; deselezionata significa conservarla. Mantenere l’associazione corretta tra riga, dichiarazione e scelta di rimozione anche quando i valori protetti sono esclusi dalla visualizzazione. Non cambiare il significato delle opzioni globali per `fill` e `stroke`.

4. **Sei pulsanti per il colore di anteprima.** Sostituire il pulsante ciclico con sei pulsanti espliciti, ciascuno con nome e indicazione visiva del colore. Usare i sei colori già presenti: Rosso `#D23741`, Blu `#235FD2`, Verde `#1E9B55`, Viola `#9641C8`, Nero `#000000`, Grigio `#828282`. Evidenziare il colore attivo. Un clic applicherà direttamente il colore scelto alle anteprime nelle cinque dimensioni esistenti: 96, 72, 32, 24 e 16 px. Il nero di prova resta disponibile: è distinto dalle dichiarazioni nere protette. Il colore di prova non verrà incorporato nell’SVG esportato.

5. **Anteprima aggiornata a ogni cambio di checkbox.** Verificare la gestione degli eventi e correggere il percorso di aggiornamento affinché ogni attivazione o disattivazione registri prima la scelta nella riga corretta, quindi rigeneri l’SVG, il testo XML e tutte le anteprime. L’aggiornamento deve avvenire subito, senza richiedere un cambio di focus o un altro comando. La causa precisa del bug sarà verificata durante l’implementazione.

## Verifiche previste

- Usare `esempio.svg` per ogni verifica che richieda un’icona.
- Controllare che il codice XML sia effettivamente mostrato con font monospace.
- Verificare che i neri aggiunti alla radice non compaiano nella complex grid e siano sempre presenti nell’SVG elaborato ed esportato.
- Attivare e disattivare ripetutamente la rimozione dei colori originali `#575756` e `#3eab3e`, controllando che le altre scelte rimangano corrette e che tutte le anteprime si aggiornino subito.
- Provare tutti i sei pulsanti, il loro stato attivo e le opzioni per il colore dinamico di `fill` e `stroke`.
- Controllare che apertura, trascinamento ed esportazione continuino a funzionare e che le verifiche esistenti sulla trasformazione restino valide.

## Passo successivo

Attendere l’approvazione dell’utente su questa proposta prima di modificare la libreria o l’interfaccia.
