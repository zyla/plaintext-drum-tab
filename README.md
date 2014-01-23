A drum tab format without significant whitespace
================================================

Easy:

    song := ( meter? ( measure ';' )* )* measure?
    meter := number '/' number '.'
    number := [0-9]+
    measure := track ( ',' track )*
    track := instrument ':' note+
    instrument := [A-Z]+
    note := number? 'T'? [WwHhQqEeSs]

(The grammar gets pretty messy for the corner cases, but you know what I mean.)

Of course, white space doesn't matter.

If meter is not specified, it's that of previous measure.
Number before note means repeated note. 'T' means triplet value (2/3 of the note time). Small letters - pauses, capital letters - notes. W - whole, H - half, Q - quarter, E - eighth, S - sixteenth.

## Example ##

To encode a typical 4/4 rock shuffle:

    4/4.
    H: 4Q,
    B: 2H,
    S: qQqQ
  
This can be easily pretty formatted for readability:

    4/4.
    H: Q Q Q Q
    B: H   H
    S: q Q q Q

But more importantly, it can be fit into just 20 characters:

    4/4.H:4Q,B:2H,S:qQqQ

Pretty cool if you want to quickly send an idea over SMS/IM, or even write something quickly on paper.

## TODO ##

 * Make a case-insensitive variant, especially for paper users.
 * Cleaner syntax (this was invented on-the-fly), retaining common sense
