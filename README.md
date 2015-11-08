# objective-c-style-guide #

:exclamation: DRAFT :exclamation:


Guida di riferimento per i progetti Objective-C in Tiknil. 
Non vuole essere l'ennesima riproposizione dello stile di stesura dei progetti in questo linguaggio, ma uno strumento utile per il team e i suoi collaboratori. 

Sentitevi liberi di dissentire da quanto abbiamo deciso di tenere come stile guida! :wink:

### References ###

Di seguito le linee guida che abbiamo consultato e a cui facciamo riferimento per la stesura della presente: 
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



### Lingua ###
Usare la lingua **Inglese** per il **codice**, quella **Italiana** per i **commenti** e la **documentazione** del codice (ove non espressamente richiesta la lingua inglese)

:+1:
```
UIColor *myColor = [UIColor whiteColor];
```
:-1: 
```
UIColor *mioColore = [UIColor whiteColor];
```

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

Per semplificare l'utilizzo dell'organizzazione del codice come descritto consigliamo di utilizzare lo *snippet* di XCode apposito come descritto nel repo ***REPO XCODE SNIPPETS***: basta digitare ```def``` quando si sta per stendere l'implementazione di una nuova classe

***INSERIRE GIF ANIMATA UTILIZO SNIPPET IN XCODE***

### Commenti ###

Per scrivere codice di qualità i commenti sono fondamentali: essi rientrano nei [requisiti non funzionali o di qualità (ISO IEC 9126)](https://it.wikipedia.org/wiki/ISO/IEC_9126) di tutti i progetti sofware all'interno della voce "Manutenibilità".

* I commenti, quando necessari, devono spiegare perché una particolare parte di codice fa qualcosa. Ogni commento che è utilizzato dev'essere sempre aggiornato o eliminato.
* Preferire codice auto-esplicativo (dando nomi significativi alle variabili e ai metodi, vedi [Naming](#naming), se possibile, rispetto ai commenti. Nel dubbio, metterli entrambi

### Naming ###

Fare riferimento alle [linee guida Apple](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-BBCHBFAH) riprese anche da [RW](https://github.com/raywenderlich/objective-c-style-guide/blob/master/README.md#naming) per cui: 

I nomi dei metodi e delle variabili devono essere descrittivi, va bene anche se sono lunghi

:+1:
```
UIButton *settingsButton;
```
:-1:
```
UIButton *setBut;
```

Le costanti devono essere *camel-case* con tutte le parole con la prima lettera maiuscola e devono iniziare con il nome della classe a cui fanno riferimento (se lo fanno).

:+1:
```
static NSTimeInterval const RWTTutorialViewControllerNavigationFadeAnimationDuration = 0.3;
```
:-1:
```
static NSTimeInterval const fadetime = 1.7;
```

I campi (`@property`) delle classi devono essere *camel-case* con la prima lettera minuscola. Preferire l'auto-sintesi dei campi piuttosto che scrivere manualmente i `@synthesize` a meno che ci sia una buona ragione. 

:+1:
```
@property (strong, nonatomic) NSString *descriptiveVariableName;
```
:-1:
```
id varnm;
```

#### Underscores ####

Quando si usano i campi (`@property`) d'istanza essi devono essere sempre richiatami usando `self.`. Questo rende più evidente in maniera visiva l'utilizzo dei campi d'istanza.

Fa eccezione l'utilizzo dei campi con *underscore* (`_variableName`) nei metodi `init` o nei metodi getter/setter che ne richiedano l'utilizzo per il corretto funzionamento.

Le variabili locali **non devono contenere underscore**.



