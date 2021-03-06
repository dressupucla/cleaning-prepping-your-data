## Regular Expressions Cheat Sheet with examples for OpenRefine

Regular Expressions can be used in OpenRefine, as well as in other applications like Python and R, to manipulate data in a more fine-grained detail.

Here is an example adapted from https://github.com/OpenRefine/OpenRefine/wiki/Understanding-Regular-Expressions (Specifically, consider we have a numbers in our dataset, like: 120.899, -0.2909, and +2.343):

We can describe these number as:
* Each optionally starts with a sign (minus or plus)
* Then it consists of a sequence of one or more digits
* Then optionally if it has a decimal part, it contains a period, followed by one or more digits

In regular expressions, this data structure is written out as:
`[-+]?[0-9]+(\.[0-9]+)?`
 
The question mark (?) denotes an optional character or group of characters. The period (.) needs to be escaped by preceding it with a backslash (\). A digit is denoted as the range of character from 0 to 9.

We have encoded a digit as [0-9] but there is a shortcut: \d. Here are more shortcuts:

* `\d`, same as [0-9]
* `\D`, same as [^0-9], meaning any character other than a digit
* `\s`, meaning any whitespace character (space, tab, new line, carriage return)
* `\S`, meaning any character other than whitespace characters
* `\w`, same as [a-zA-Z_0-9], meaning any character that can be part of a word (where the meaning of "word" is more liberal than an English word)
* `\W`, meaning any non-word character
* `.` meaning any single character

Note that any character that is used to describe patterns within regular expressions must be escaped. For example, if you want to say "a period character" rather than "any character", then you must write \. because just writing . means "any character". 

EXAMPLE USAGE FOR REGULAR EXPRESSIONS IN OPEN REFINE

In the column titled "column" in our Carteles.csv, you want to replace all instances of “in” with "inches." To do so, create a custom text facet and then in the popup box enter: `value.replace("in", "inches")`

Or, if you want to remove "in" entirely: `value.replace("in", "")`

Or, if you want to remove the spaces entirely: `value.replace(/\s+/, "")`
