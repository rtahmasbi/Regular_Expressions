
Regular expressions are **case sensitive**; lower case `/s/` is distinct from upper case `/S/`. We can solve this problem with the use of the square braces `[ and ]`: `/[wW]oodchuck/`

`/[abc]/` : ‘a’, ‘b’, or ‘c’

`/[1234567890]/`: any digit

`/[2-5]/` 2, 3, 4, or 5

`/[A-Z]/` an upper case letter

`/[a-z]/` a lower case letter

`/[0-9]/` a single digit

The square braces can also be used to specify what a single character cannot be,
by use of the caret `^`.

`/[^A-Z]/` not an upper case letter

`/[^Ss]/` neither ‘S’ nor ‘s’

`/[^\.]/` not a period

`/[e^]/` either ‘e’ or ‘^’ “look up^now”

`/a^b/` the pattern ‘a^b’ “look up a^b now”


`/?/`, which means “the preceding character or nothing”. We can think of the question mark as meaning “zero or one instances of the
previous character”.


`/woodchucks?/` woodchuck or woodchucks

`/colou?r/` color or colour



The Kleene star `*` (pronounced “cleany star”) means “zero or more occurrences of the immediately previous character or regular expression”. So `/a*/` means “any string of zero or more a's”. This will match `a` or `aaaaaa`.

So the regular expression for matching one or more a is `/aa*/`, meaning one `a` followed by zero or more a's.


So `/[ab]*/` means “zero or more a’s or b’s”. This will match strings like `aaaa` or `ababab` or `bbbb`.


An integer (a string of digits) is thus `/[0-9][0-9]*/` and not `/[0-9]*/`.


Kleene +, which means “one or more occurrences of the immediately preceding character or regular expression”. Thus, the expression `/[0-9]+/` is the normal way to specify “a sequence of digits”.


One very important special character is the period `(/./)`, a wildcard expression
that matches any single character (except a carriage return).

`/beg.n/` any character between beg and n `begin`, `beg’n`, `begun`

Anchors are special characters that anchor regular expressions to particular places
in a string. The most common anchors are the caret `^` and the dollar sign `$`.


The caret `^` matches the start of a line. The pattern `/^The/` matches the word The only at the start of a line. Thus, the caret `^` has three uses: to match the start of a line, to indicate
a negation inside of square brackets, and just to mean a caret.

The dollar sign `$` matches the end of a line.

`/^The dog\.$/` matches a line that contains only the phrase _The dog._


`\b` matches a word boundary, and `\B` matches a non-boundary. Thus, `/\bthe\b/` matches the word _the_ but not the word _other_.

`/\b99\b/` 9 and not 299. But it will match 99 in $99 (since 99 follows a dollar sign ($), which is not a digit, underscore, or letter).


## 2.1.2 Disjunction, Grouping, and Precedence
disjunction operator, also called the pipe symbol `|`.

So the pattern `/gupp(y|ies)/` would specify that we meant the disjunction only to apply to the suffixes y and ies.
