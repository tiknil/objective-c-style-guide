# objective-c-style-guide #

:exclamation: DRAFT :exclamation:


Guida di riferimento per i progetti Objective-C in Tiknil. 
Non vuole essere l'ennesima riproposizione dello stile di stesura dei progetti in questo linguaggio, ma uno strumento utile per il team e i suoi collaboratori. 

Sentitevi liberi di dissentire da quanto abbiamo deciso di tenere come stile guida! :wink:

### TL;DR ###

Troppo lunga da leggere? E' solo l'ennesima guida di stile di Obj-C? 
Ok, passiamo al dunque, nerd: usa i tool che ti elenchiamo per cominciare a 'subire' un po' di codice di qualità: 

1) [XCode snippets](https://github.com/tiknil/xcode-snippets) - dovresti leggere perché usarli, almeno

2) Installa `BBUncrustifyPlugin` tramite [Alcatraz](http://alcatraz.io/) e usa il file `uncrustify.cfg` che trovi nel presente repo. Tranquilli, è tutto ben descritto in [Tools](#tools).

### References ###

Di seguito le linee guida che abbiamo consultato e a cui facciamo riferimento per la stesura di questo documento: 
* [Apple coding guidelines](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html)
* [Ray Wenderlich Obj-C style guide](https://github.com/raywenderlich/objective-c-style-guide)
* [NY Times Obj-C style guide](https://github.com/NYTimes/objective-c-style-guide)
* [GitHub Obj-C style guide](https://github.com/github/objective-c-style-guide)
* [Google Obj-C style guide](https://google.github.io/styleguide/objcguide.xml)

### Concetti di base ###

Perché abbiamo preso certe scelte e non altre? Ecco i concetti che guidano alcune scelte esposte in questa guida (in ordine non per forza di priorità): 
* [Bellezza](https://it.wikipedia.org/wiki/Bellezza) e stile uniforme, anche nel codice
* Comprensibilità del codice da chiunque
* Velocità di scrittura del codice
* Produzione della documentazione in Italiano
* Somiglianze con altri linguaggi che utilizziamo per i progetti
* Abitudini nostre (in via di miglioramento)

### Sommario ###
1. [Lingua](#lingua)
2. [Organizzazione](#organizzazione)
3. [Commenti](#commenti)
4. [Naming](#naming)
  * [Underscores](#underscores)
  * [Categories](#categories)

[Tools](#tools)

### Lingua ###
Usare la lingua **Inglese** per il **codice**, quella **Italiana** per i **commenti** e la **documentazione** del codice (ove non espressamente richiesta la lingua inglese)

:+1: `UIColor *myColor = [UIColor whiteColor];`

:-1: `UIColor *mioColore = [UIColor whiteColor];`

### Organizzazione ###

Raccomandato l'uso dei ```#pragma mark```per raggruppare i metodi in gruppi funzionali e legati all'implementazione dei protocolli/delegati seguendo la struttura seguente (da [RW Obj-C style guide](https://github.com/raywenderlich/objective-c-style-guide)): 

```
#pragma mark - Lifecycle

- (instancetype)init {}
- (void)dealloc {}
- (void)viewDidLoad {}
- (void)viewWillAppear:(BOOL)animated {}
- (void)didReceiveMemoryWarning {}

#pragma mark - Custom Accessors

- (void)setCustomProperty:(id)value {}
- (id)customProperty {}

#pragma mark - IBActions

- (IBAction)submitData:(id)sender {}

#pragma mark - Public

- (void)publicMethod {}

#pragma mark - Private

- (void)privateMethod {}

#pragma mark - Protocol conformance
#pragma mark - UITextFieldDelegate
#pragma mark - UITableViewDataSource
#pragma mark - UITableViewDelegate

#pragma mark - NSCopying

- (id)copyWithZone:(NSZone *)zone {}

#pragma mark - NSObject

- (NSString *)description {}
```

Per semplificare l'utilizzo dell'organizzazione del codice come descritto consigliamo di utilizzare lo *snippet* di XCode apposito come descritto nel repo [Xcode-snippets](https://github.com/tiknil/xcode-snippets) basta digitare ```def``` quando si sta per stendere l'implementazione di una nuova classe

![def code snippet](https://github.com/tiknil/xcode-snippets/blob/master/images/def_code_snippet.gif)

### Commenti ###

Per scrivere codice di qualità i commenti sono fondamentali: essi rientrano nei [requisiti non funzionali o di qualità (ISO IEC 9126)](https://it.wikipedia.org/wiki/ISO/IEC_9126) di tutti i progetti sofware all'interno della voce "Manutenibilità".

* I commenti, quando necessari, devono spiegare perché una particolare parte di codice fa qualcosa. Ogni commento che è utilizzato dev'essere sempre aggiornato o eliminato.
* Preferire codice auto-esplicativo (dando nomi significativi alle variabili e ai metodi, vedi [Naming](#naming), se possibile, rispetto ai commenti. Nel dubbio, metterli entrambi.

Come commentare? Ecco un ottimo (e breve) articolo su NSHipster relativo alla documentazione Obj-C [Documentation](http://nshipster.com/documentation/)
```
/**
 Questo è un commento
 */
```

e

```
/**
 Questo è il commento alla dichiarazione di questo metodo che ha come parametro paramValue e che ritorna come risultato resultValue
 @param paramValue il parametro passato a questo metodo
 @result resultValue il risultato che viene ritornato x o y in base al parametro
 */
```

Non sei sicuro di riuscire a ricordarti sempre come scrivere i commenti? Fatti aiutare dagli [snippets `com`...](https://github.com/tiknil/xcode-snippets)!

### Naming ###

Fare riferimento alle [linee guida Apple](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-BBCHBFAH) riprese anche da [RW](https://github.com/raywenderlich/objective-c-style-guide/blob/master/README.md#naming) per cui: 

I nomi dei metodi e delle variabili devono essere descrittivi, va bene anche se sono lunghi

:+1: `UIButton *settingsButton;`

:-1: `UIButton *setBut;`

Le costanti devono essere *camel-case* con tutte le parole con la prima lettera maiuscola e devono iniziare con il nome della classe a cui fanno riferimento (se lo fanno).

:+1: `static NSTimeInterval const RWTTutorialViewControllerNavigationFadeAnimationDuration = 0.3;`

:-1: `static NSTimeInterval const fadetime = 1.7;`

I campi (`@property`) delle classi devono essere *camel-case* con la prima lettera minuscola. Preferire l'auto-sintesi dei campi piuttosto che scrivere manualmente i `@synthesize` a meno che ci sia una buona ragione. 

:+1: `@property (strong, nonatomic) NSString *descriptiveVariableName;`

:-1: `id varnm;`

#### Underscores ####

Quando si usano i campi (`@property`) d'istanza essi devono essere sempre richiatami usando `self.`. Questo rende più evidente in maniera visiva l'utilizzo dei campi d'istanza.

Fa eccezione l'utilizzo dei campi con *underscore* (`_variableName`) nei metodi `init` o nei metodi getter/setter che ne richiedano l'utilizzo per il corretto funzionamento.

Le variabili locali **non devono contenere underscore**.

#### Categories ####

Le categories devono avere nomi che ne definiscano la funzionalità. Attenzione a non creare categories che fanno uso di altre categories (il debug potrebbe diventare arduo).

:+1: `@interface NSString (StringEncodingDetection)`

:-1: `@interface NSString (Utilities)`

_I metodi delle category devono avere sempre il prefisso seguito da underscore._ Questo limita la possibilità di creare eventuali duplicati di metodi esistenti tra le varie librerie.

`- (NSStringEncoding) sed_detectStringEncoding:(NSString*)string;`

Se hai necessità di esporre dei metodi privati per delle sottoclassi o per fare test crea una categories chiamata `Class+Private`

### Tools ###

Per noi è importante trovare i tool che ci permettano di mantenere certe scelte in modo costante e coerente di progetto in progetto. Partecipando ad un interessante *talk* di Anastasia Kazakova (@anastasiak2512) alla #Pragma conf 2015 a Firenze abbiamo visto che IDE come AppCode integrano strumenti per la formattazione del codice in modo avanzato ma tramite alcuni plugin e risorse è possibile avere queste funzionalità anche su XCode. 

Quello che abbiamo trovato più completo e facile da capire è [Uncrustify](http://uncrustify.sourceforge.net/) che in XCode è facilmente intergrabile tramite il plugin [BBUncrustifyPlugin](https://github.com/benoitsan/BBUncrustifyPlugin-Xcode), installabile anch'esso tramite [Alcatraz](http://alcatraz.io/).

Una volta installato basta andare in `Edit > Format Code > BBUncrustifyPlugin preferences`, scegliere come formatter `Uncrustify` e alla voce `Clang style` scegliere `Custom Style (File)` (se lo desiderate, altrimenti scegliete il formattatore che più vi [aggrada](https://www.youtube.com/watch?v=b3mGYIgR5_c)).

Alla voce `Configuration File` dunque scegliere `Create Configuration File` e il vostro editor di testo preferito (sarà indubbiamente [Sublime Text](http://www.sublimetext.com/).

Per utilizzare lo stile delineato in questa guida basta prendere il file `uncrustify.cfg` e copiarlo in una qualsiasi cartella padre della cartella del progetto di XCode che avete aperto. Il consiglio è di avere il file `uncrustify.cfg` nella cartella root dei vostri progetti iOS/OSX. 

Se volete fare le cose per bene, fate così: 
1) Fate un fork di questo repository e scaricatelo in locale nella cartella `$OBJ_C_STYLE_GUIDE_REPO`
2) Quindi create un link simbolico al file `uncrustify.cfg` nella cartella root dei vostri progetti iOS/OSX
```
ln -s ~/App/iOS/uncrustify.cfg ~/Development/GitHub/objective-c-style-guide/uncrustify.cfg
```
