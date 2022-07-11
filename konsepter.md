# Teoretiske konsepter
Funksjonell programmering er basert på formell logikk og matematikk. Det fører til at mange viktige konsepter er definert på en ganske abstrakt og lite inviterende måte. De abstrakte beskrivelsene fører imidlertid til garantier for hvordan de ulike strukturene fungerer, og er såpass generelle at de kan brukes for å garantere oppførselen til mange ulike datastrukturer og programmeringsmønster.

## Monader
Monader er data satt i en kontekst, ofte implementert som en datatype som wrapper en verdi. For at en struktur skal være en monade må det være mulig å pakke verdier inn i monaden, og operere på de innpakkede verdiene med funksjoner som tar en monade og returnerer en ny. Ettersom monadiske funksjoner returnerer nye monader, er det mulig å koble dem sammen for å lage en kjede med operasjoner der konteksten bevares.

### Definisjon
Vi kan definere en monade som `m a`, der `a` er en verdi og `m` representerer en kontekst. Disse to verdiene sammen definerer monaden. For å pakke en verdi `a` inn i en monade `m a` brukes en funksjon som ofte kalles `return`. `return a` vil returnere en verdi av typen `m a`. ***Merk at `return`-funksjonen i utgangspunktet er noe annet enn nøkkelordet `return`*** som brukes i imperativ programering for å definere returverdien til en funksjon. For å operere på en monade brukes funksjonen `bind`. Bind tar en monade og en funksjon som pakker en verdi inn i en monade som en parameter. `bind` tar deretter og "pakker ut" verdien i monaden den fikk, og sender den til funksjonen.

### Eksempel
En monade som er mye brukt er Maybe-monaden. Maybe-monaden brukes for å sette en verdi i konteksten "verdi eller `null`". I kotlin er den kjent som en "nullbar variabel", og vi bruker kotlins implementasjon som eksempel.

I kotlin blir `return` implesitt kalt når man definerer en ny variabel som nullable:

```
var nullbar_variabel: String? = "abc"
```
Kan også tolkes som utsagnet

```
  return_nullbar "abc"
```

Der vi definerer `return_nullbar` som `return`-funksjonen til monadetypen "nullbar variabel". Bind-funksjonen dukker opp som operatoren `?.` om man prøver å hente ut et felt eller kalle en funksjon på den nullbare variabelen:
```
   var nullbar_lengde: Int? = nullbar_variabel?.length
```

Merk at returtypen til `?.` er en ny nullbar variabel. Den oppfører seg derfor som `bind` skal gjøre. Vi kan gjøre sammenhengen enda mer eksplisitt ved å skrive om `?.` til en prefiksfunksjon og kalle den `bind_nullbar`:

```
  var nullbar_lengde: Int? = bind_nullbar(nullbar, length)
```

Vi ser da at bind_nullbar tar en nullbar verdi og en funksjon som virker på verdien som er pakket inn i den nullbare verdien, og returnerer en ny nullbar verdi. `?.` tar seg av å sjekke om den nullbare verdien faktisk inneholder en verdi eller er `null`, og bruker konteksten til å enten kalle funksjonen `length` eller å videresende konteksten `null`

## Functorer

## Monoider

## Høyerenivås programmering

## Delvis applikasjon og currying

# Eksempler

## Array
*** Type

## Linser

## Either
***Type: Monade***
***Formål: Håndtere beregninger med to typer utfall***

## Promise
***Type: Monade?***
***Formål: asynkrone og usikre beregninger***

## Nullable

## FlatMap?

