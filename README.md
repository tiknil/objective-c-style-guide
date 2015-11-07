# objective-c-style-guide #

Guida di riferimento per i progetti Objective-C in Tiknil. 
Non vuole essere l'ennesima riproposizione dello stile di stesura dei progetti in questo linguaggio, ma uno strumento utile per il team e i suoi collaboratori. 

Sentitevi liberi di dissentire da quanto abbiamo deciso di tenere come stile guida! ;-)

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

*** INSERIRE GIF ANIMATA UTILIZO SNIPPET IN XCODE ***

### Commenti ###

Per scrivere codice di qualità i commenti sono fondamentali: essi rientrano nei [requisiti non funzionali o di qualità](https://it.wikipedia.org/wiki/ISO/IEC_9126) di tutti i progetti sofware all'interno della voce "Manutenibilità".

* I commenti, quando necessari, devono spiegare perché una particolare parte di codice fa qualcosa. Ogni commento che è utilizzato dev'essere sempre aggiornato o eliminato.
* I commenti 
Block comments should generally be avoided, as code should be as self-documenting as possible, with only the need for intermittent, few-line explanations. Exception: This does not apply to those comments used to generate documentation.

