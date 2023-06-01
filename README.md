# GDB-debugger-in-C
Istruzioni Base per l'utilizzo del tool di debuggind in C : GDB


gdb: permette di eseguire il programma passo passo e verificare i valori delle variabili

Per abilitare il debugging compilare il codice C con opzione **-g**

```
$ gcc -g -Wall -pedantic main.c -o main
```
Per avviare il debugger usare il comando

**
gdb [opzioni] eseguibile [opzioni eseguibile]
**

```
gdb main
```

Una volta avviato usiamo il comando run per eseguire il programma. Per interrompere la sessione di debugging usare il comando **quit**

Possiamo definire dei punti nel programma dove fermare l'esecuzione per analizzare lo stato delle variabili:

* **Breakpoint** un punto nel codice dove fermarsi
*  **Whatchpoint** Una variabile da monitorare- il prog di ferma quando la variabile cambia

## GDB - Breackpoint
Settare un breakpoint:
* comando b seguito da numeri di riga o nome funzione (b 6 - break alla riga 6, b main.c:6 - break nel file main.c in riga 6, b push - break sulla prima istr della funzione push.

Rimuovere un breakpoint:
* delete n - rimuove breakpoint numero n
* enable/disable n - on/off breakpoint n

## GDB - whatchpoint
Settare un watchpoint:
* whatch seguito dal nome della variabile (es. watch a) ma questo funziona solo nello scope della variabile

Rimuovere un watchpoint
* delete n - rimuove watchpoint numero n
* enable/disable n - on/off watchpoint n

## GDB - controllare lo stato dell'applicazione
* comando p (print) stampa il contenuto di una variabile 
- p x - stampa il valore di x
- p &x - stampa l'indirizzo di x
- p a[3]@5 - stampa 5 valori nell'array **a** a partire da lterzo valore.
* comando bt - stampa la pila dei record di attivazione (backtrace) 
* comando x - stampa il valore memorizzato ad un indirizzo di memoria dato

## GDB - continuare l'esecuzione
Una volta fermati su un breackpoint/watchpoint di solito si vuole continuare l'esecuzione

- fino al prossimo breakpoint: **continue**
- un'istruzione avanti:
  - senza entrare nelle funzioni: **next**
  - entrando nelle chiamate di funzioni: **step**
- Fino all'uscita dalla chiamata di funzione corrente: **finish**
- 
