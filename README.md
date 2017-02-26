# Rechnerorganisation - Hausaufgabe MIPS-Assembler

Die Hausaufgaben sind unterteilt in..

- [x] [Bilder laden und speichern](#bilder-laden-und-speichern-7-punkte) (7 Punkte)
- [x] [Verringern der Bildauflösung](verringern-der-bildaufl%C3%B6sung-7-punkte) (7 Punkte)
- [x] [Verringern der Farbtiefe](#verringern-der-farbtiefe-3-punkte) (3 Punkte)
- [x] [Betrachtungsaufgabe](#betrachtungsaufgabe-3-punkte) (3 Punkte)
- [x] Auf den tubit Rechnerpools testen.

`qtspim` im root Verzeichnis starten! Ansonsten stimmen die Pfade nicht.
[Anleitung](https://isis.tu-berlin.de/pluginfile.php/558943/mod_forum/attachment/241471/QtSpim_Leitfaden.pdf) für `qtspim` auf den tubit Rechnerpools.

## Bilder laden und speichern (7 Punkte)
```mips
load_img

@param  $a0 pointer to filename
@return $v0 image content <8bit segments>
@return $v1 header information <[0]width [1]height [2]brightness>
```
```mips
store_img

@param  $a0 image content <8bit segments>
@param  $a1 header information <[0]width [1]height [2]brightness>
@param  $a2 filename pointer
@return void
```

## Verringern der Bildauflösung (7 Punkte)
```mips
interpolate2

@param  $a0 image content <8bit segments>
@param  $a1 header information <[0]width [1]height [2]brightness>
@return void
```

```mips
interpolate
~ calls interpolate2

@param  $a0 image content <8bit segments>
@param  $a1 header information <[0]width [1]height [2]brightness>
@param  $a2 power (2^n) of reduction
@return void
```

## Verringern der Farbtiefe (3 Punkte)
```mips
quantize

@param  $a0 image content <8bit segments>
@param  $a1 header information <[0]width [1]height [2]brightness>
@param  $a2 quantize factor
@return void
```

## Betrachtungsaufgabe (3 Punkte)
`wood.pgm` First quantize then interpolate:
> ![wood_q_then_i (local)](images/Aufgabe4/wood_q_then_i.png "First quantize then interpolate")

`wood.pgm` First interpolate then quantize:
> ![wood_i_then_q (local)](images/Aufgabe4/wood_i_then_q.png "First interpolate then quantize")


`worn.pgm` First quantize then interpolate:
> ![worn_q_then_i (local)](images/Aufgabe4/worn_q_then_i.png "First quantize then interpolate")

`worn.pgm` First interpolate then quantize:
> ![worn_i_then_q (local)](images/Aufgabe4/worn_i_then_q.png "First interpolate then quantize")

`sky.pgm` First quantize then interpolate:
> ![sky_q_then_i (local)](images/Aufgabe4/sky_q_then_i.png "First quantize then interpolate")

`sky.pgm` First interpolate then quantize:
> ![sky_i_then_q (local)](images/Aufgabe4/sky_i_then_q.png "First interpolate then quantize")


Wie an den Bildern zu erkennen ist (`Unteraufgabe 1`), gehen mehr Informationen im
Bild verloren, wenn zuerst die Farbtiefe verringert wird, bevor der Auflösung.
Das liegt daran, dass beim Verringern der Farbtiefe das Spektrum der Farben
reduziert wird (verlust von signifikanten Bits), sodass beim verringern der Auflösung,
bei dem ziehen des Mittelwerts, schon ein signifikanter Informationsverlust
statt gefunden hat.

### References
- [1] http://spimsimulator.sourceforge.net/HP_AppA.pdf
~ Assemblers, Linkers, and the SPIM Simulator
- [2] http://stackoverflow.com/questions/22588905/mips-dynamic-memory-allocation-using-sbrk
- [3] https://www.cs.umd.edu/class/sum2003/cmsc311/Notes/Mips/pseudo.html
- [4] https://www.cs.ucsb.edu/~franklin/64/lectures/mipsassemblytutorial.pdf
- [5] http://fxr.watson.org/fxr/source/sys/fcntl.h?im=10#L65
~ file open flags (O_RDONLY|O_WRONLY|O_RDWR|O_ACCMODE)
- [6] https://www.cs.umd.edu/class/sum2003/cmsc311/Notes/Mips/dataseg.html
~ Data and Text Segment
- [7] https://de.wikipedia.org/wiki/Portable_Anymap
- [8] http://www.cs.umd.edu/class/sum2003/cmsc311/Notes/Mips/jump.html
~ Conditional and Unconditional Jumps
- [9] https://www.doc.ic.ac.uk/lab/secondyear/spim/node16.html
~ Branch and Jump Instructions
- [10] http://www.programmingforums.org/thread39778.html
~ itoa procedure (assembly MIPS)
- [11] http://stackoverflow.com/questions/4580166/length-of-array-in-mips
~ length of array in mips
- [12] http://stackoverflow.com/questions/9180983/mips-memory-management
~ mips memory management
- [13] http://stackoverflow.com/questions/18812319/multiplication-using-logical-shifts-in-mips-assembly
~ Multiplication using Logical shifts in Mips assembly
