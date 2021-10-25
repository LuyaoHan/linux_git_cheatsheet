# Subtitutition
	s/<string_to_look_for>/<string_for_substitution>/
	
# Subtitutition all (g)lobal matches 
	s/<string_to_look_for>/<string_for_substitution>/g

# Subtitutition (i)gnore cases
	s/<string_to_look_for>/<string_for_substitution>/i

# Metacharacters 

	0) Match any characters

	1) Match any chars in either a,b,c, etc.

		[abc]

		[a-z0-9]

	2) Match any chars other than a,b,c, etc.

		[^abc]

		[^a-z]

		(!) "^" means XOR, to reverse.

	3) Match all integer numbers

		\d

		[0-9]

	4) Match everything other than integer

		\D

	5) Match all hex numbers

		\x

		[0-9A-Fa-f]

	6) Match everything other than hex

		\X

		[^0-9A-Fa-f]

	7) Match all valid word letters

		\w

		[0-9A-Za-z]

	8) Match all tabs

		\t

	9) Match all spaces

		\s

	10) Match non-space characters

		\S

	11) Match anything

		\*

	12) Match special characters

		\*

		\.

		\/

		\\

		\[

# Metacharacters for specifying numbers of characters to match

	1) \+ : to match one or more

# Metacharacters for positions matching

	1) $  : end of line

	2) ^  : head of line

	3) \< : head of a word

	4) \> : end of a word

# Match and change lower/upper cases

	%s/[Hh]elp/HELP/g

	(!) "s" for "substitute"

	(!) "g" for "global"

# Match multiple continuous spaces and substitute with only one

	%s/ \+/ /g

# Match empty lines and delete

	g/^$/d

	(!) "g" for "global"

	(!) "d" for delete"

# Delete lines with contains <target>

	g/ERROR/d

# Delete all the useless spaces in front of every lines.

	%s/^ *//g

# Match from the beginning to the first space -- " "

	regex = "^\S+"

# Count the number of words (between each space)
	
	regex = "[a-z]+"

