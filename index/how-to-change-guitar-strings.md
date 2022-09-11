***PROGRAM How to change guitar strings for dummies***

**This guide will cover how to remove/replace/tune a new set of standard .09-.42 guitar strings onto a 6 string guitar**

*Initialize*

**Get: Materials**

>Strings [.42, .32, .24, .16, .11, .09]
>
>Wirecutters

**Case: Guitar/Bridge/Headstock Type**

> i. Is it an electric or acoustic?
> 
>> a) if acoustic assume peg bridge and 3x3 headstock and jump to "Remove old strings"
>> 
>> b) else if electric continue with next step
>> 
> ii. Is the headstock inline 6 or 3x3?
> 
> iii. Is the bridge a through body, top load, or peg?

*Functions*

**Function: snip**

> i. Using a pair of wire cutters: cut string.
> 

**Function: removeOldStrings**

> i. Remove string fragments from bridge
> 
>> a) If thru body style, remove from back of guitar
>> 
>> b) else if top load, remove from the bottom of the bridge
>> 
>> c) else if peg, remove peg, then remove string
>> 
> ii. Remove string fragments from headstock (loop until all string fragments removed from headstock)
> 
>> a) Unwind string from tuning peg and remove (process is the same for both inline 6 and 3x3)

**Function: installNewStrings**

> i. Thread in new strings  to bridge (loop until all strings are threaded into bridge)
> 
>> a) From bottom (near the volume/tone knobs) 
>> 
>> b) To the top (near the strap button) 
>> 
>> c) With the .09 gauge being at the bottom and the .42 gauge being at the top
>> 
>>> 1) if thru body style, thread from the back
>>> 
>>> 2) else if top load, thread from the bottom of the bridge
>>> 
>>> 3) else if peg, insert string and replace peg on top to secure
>>> 
> ii. Thread into tuning pegs (loop until all strings are threaded into tuning pegs)
> 
>> a) if inline 6 thread .42 in the nearest and repeat with decending gauges in order down the line to the last one with .09 gauge
>> 
>> b) else if 3x3 thread .42 in the nearest tuning peg on the left, repeat process clockwise for all tuning pegs
>> 
> iii. Turn tuning pegs counter-clockwise on left side of headstock (else if 3x3: clockwise on right side) to tension the strings

**Function: tuneGuitar**

> i. Tune up (clockwise) tune down (counter-clockwise) else if 3x3 reverse rotation for d), e), f)
> 
>> a) (.42 gauge) = (E) 82.41Hz
>> 
>> b) (.32 gauge) = (A) 110.00Hz
>> 
>> c) (.24 gauge) = (D) 146.83Hz
>> 
>> d) (.16 gauge) = (G) 196.00Hz
>> 
>> e) (.11 gauge) = (B) 246.94Hz
>> 
>> f) (.09 gauge) = (E) 329.63Hz
>> 
> ii. Trim any excess pieces from headstock with wire cutters
> 
> iii. Rock on padre/madre

```VARIABLES

strings = [.42, .32, .24, .16, .11, .09]
tune = [82.41Hz, 110.00Hz, 146.83Hz, 196.00Hz, 246.94Hz, 329.63Hz]
myGuitar = (userGuitar)
headstock = myGuitar.top
bridge = myGuitar.bottom
knobs = stings.anchor(headstock)
peg = strings.anchor(bridge)
pitch = ()Hz
cut = string / string

FUNCTIONS

snip(myGuitar.strings) {
    wirecutters.cut(strings)
}

headstockDetermine(myGuitar) {
    IF myGuitar.headstock = inline6
        hsType = inline6
        inline6 = right.knobs
    ELSE 
        hsType = 3x3
        3x3 = right.knobs + left.knobs
}

bridgeDetermine(myGuitar) {
    IF myGuitar.bridge = thrubody
        bType = thruBody
    ELSE IF myGuitar.bridge = topLoad
        bType = topLoad
    ELSE
        bType = pegBridge
}

removeOldStringsHS(myGuitar.headstock) {
    unwind.headstock(strings)
    remove.headstock(strings)
}

removeOldStringsB(myGuitar.bridge(bType)) {
    IF bType = thruBody
        remove.access.back(strings)
    ELSE IF bType = topLoad
        remove.access.bridge(strings)
    ELSE 
        remove.access.peg(strings)
}

installNewStringsHS(myGuitar.headstock(hsType)) {
    IF hsType = inline6
        thread.inline6(strings)
    ELSE
        thread.3x3(stings) {
            thread.right.knobs(.42, .32, .24)
            thread.left.knobs(.16, .11, .09)
        }
}

installNewStringsB(myGuitar.headstock(hsType)) {
    IF bType = thruBofy
        thread.acces.back(strings)
    ELSE IF bType = topLoad
        thread.access.bridge(strings)
    ELSE 
        thread.access.peg(strings)
}

tuneGuitar(myGuitar.strings(hsType)) {
    IF hsType = inline6
        WHILE strings.pitch =! tune.pitch
            rotate.left(knobs) pitch++
            rotate.right(knobs) pitch--
        END WHILE
    ELSE
        WHILE strings.pitch =! tune.pitch
            rotate.left(knobs(.42, .32, .24)) pitch++
            rotate.right(knobs(.42, .32, .24)) pitch--
            rotate.right(knobs(.16, .11, .09)) pitch++
            rotate.left(knobs(.16, .11, .09)) pitch--
        END WHILE
}

guitarDetermine(myGuitar) {
    IF myGuitar = electric THEN
        RUN (headstockDetermine)
            (bridgeStyleDetermine)
    ELSE IF myGuitar = acoustic
        RUN (snip) FOR strings
            (removeOldStrings.3x3.pegBridge) FOR strings
            (installNewStrings.3x3.pegBridge) FOR strings
            WHILE stings.pitch =! tune.pitch
                RUN (tuneGuitar.3x3)
}

EXAMPLE RUN

determineGuitar('Fender Stratocaster')

headstockDetermine('Fender Stratocaster')

bridgeDetermine('Fender Stratocaster')

snip('Fender Stratocaster'.strings)

removeOldStringsHS('Fender Stratocaster'.headstock)

removeOldStringsB('Fender Stratocaster'.bridge(thruBody))

installNewStringsHS('Fender Stratocaster'.headstock(inline6))

installNewStringsB('Fender Stratocaster'.headstock(thurBody))

tuneGuitar('Fender Stratocaster'.strings(inline6))
```
