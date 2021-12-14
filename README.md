# Lezione Flex

### Appunti

Quando si usano i trasform si ha una situazione tipo position:relative, si muove il contenuto, ma l'ingombro rimane lo stesso.

### Flexbox

Nuovo modo per disegnare layout delle nostre pagine con i display inline-block.

Un contenitore definito come "flex" fare centraggi diventa uno scherzo. Delega la maggiorparte dei compiti al browser.

Non tutti i browser hanno implementato flexbox, quindi consiglio usare sempre i settings piu' facili. Usare il sito caniuse molto con flex. 

Flexbox puo' essere usato in accoppiata con gli altri strumenti che gia' conosciamo. In alcune occasioni sono piu' semplici gli strumenti che gia' conosciamo.

Non e' una regola CSS! E' un vero e proprio strumento che contiene istruzioni, e' una suite che ci viene offerta.

Si definisce con display:flex (come displa block, inline ecc), flex si applica al contenitore padre che si chiama "container-flex", i figli diventeranno automaticamente "flex-item".

[Il display flex inline fa si che il container sia un container per i figli, ma un inline block per il resto della pagina]

Le proprieta' flex non si ereditano in alcun modo, i flex-item se hanno contenuto non sono flex-container, ma va specificato. quindi

<div class="container-flex">
	<div class="item"></div>
	<div class="item"></div> 
	<div class="item">
		<div class="item">
		<div class="item">
		<div class="item">
	</div> se volessi renderlo un container-flex devo specificarlo di nuovo!
</div>	 

.container-flex{
	display:flex;
}


I vantaggi sono che gli item possono essere o disposti orizzontalmente o verticalmente usando una regola.
Altro vantaggio che gli elementi possono essere centrati senza difficolta'.
Altro vantaggio, nella maggiorparte dei casi gli item hanno dimensioni flessibili. Ad esempio potrei dire che il mio item abbia delle dimensioni che vorrei, oppure in proporzione ad esempoio dire che il secondo item asbbia il doppio delle dimensioni del primo. Flex gestisce flessibilmente le dimensioni.

L'allineamento viene visto in due direzioni: asse x e assey, chiamati MAIN AXIS che e' x. CROSS AXIS che e' y.
flex-direction:row, dispone in sulle X.
flex-direction:column, sulle y
Gli assi si invertono, in row x e y come passiamo, in column y diventa x e viceversa.
La rilevanza principale che se ad esempio diciamo che la width del primo item in row e' 100px, tutto funzioona, ma in column diventa complesso invertendosi gli assi.
Si usa quindi flex-basis per riferirsi al MAIN AXIS.
La dimensione del MAIN AXIS si chiama MAIN SIZE
La dimensione del CROOS AXIS si chiama CROSS SIZE.

I div item si allineano come fossero inline-block ,ma non lo sono!
Con row vanno sulla riga, column verticalmente. 
Esiste row-reverse che allinea da destra a sinistra, quindi partendo da destra. 

Si possono muovere elementi sull'asse del main axys e cross axys.
Si applica al container MAIN AXYSla regola justify-content: flex-start, che le allinea a sinistra (se e' row, row-reverse al contrario).  flex-end le allinea a destra.
Se invece CROSS allign-items:flex-start o flex-end.

Lungo il main axys abbiamo inoltre
* flex-start: allinea a sinstra
* flex-end a destra
* center centra gli elementi
* space-between, dice che uno spazio tra gli elementi sia uguale
* space around aggiunge tipo margine, comunque slides hanno gli esempi


Lungo il cross axys
* flex-start
* flex-end
* center
* stretch, comportamento predefinito che fa si che tutti gli elementi del nostro container abbiano la stessa lunghezza. Finalmente addio altezze fisse.
* baseline, se negli itam c'e' un testo, fissa una linea su cui fissare il testo.

Flexbox nativamente mette tutto sulla stessa riga, anche se sotto abbiamo  sspazio a disposizione.
Con 
* nowrap e' il default
* wrap va su piu' linee

Il centraggio completo all'interno della pagina si fa metto display:flex al container e margin:auto all'item.

Per riferirsi al figlio con la width oppure flex-basis in percentuale, pixel come vogiamo. Vengono fuori problemi, se gli spazi non tornano flex non prende in considerazione il flex-basis. 

Flex-basis non e' obbligatorio, indica il nostro desiderio che un elemento se possibile sia di una determinata lunghezza. Con flex-grow dico il 100% dello spazio me lo dividi e distribuisci come dico io. flex-grow 1 prende una parte, flex-grow 2 due parti ad esempio.

Flex-shrink fa il contrario, lo spazio mancante lo sottrai ad ogni elemento. 

#### Usare flexbox per spostare un elemento dall'essere un numero 4 ad un numero 1.

Spostavamo il div o elemento fino ad ora. Abbiamo il comando order: e specifichiamo il posizionamento, per metterlo all'inizio -1.