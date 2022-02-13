# Subtitutition
	
	s/<string_to_look_for>/<string_for_substitution>/
	
# Subtitutition all (g)lobal matches 
	
	s/<string_to_look_for>/<string_for_substitution>/g

# Subtitutition (i)gnore cases
	
	s/<string_to_look_for>/<string_for_substitution>/i

# Match any characters
	
	.*

# (Perl-specific)

	my $result = $source_string =~ m/(<search_string>)/;

	(!) Note that the parentheses are needed to actually capture the match.

# Match any chars in either a,b,c, etc.

		[abc]

		[a-z0-9]

# Match any chars other than a,b,c, etc.

		[^abc]

		[^a-z]

		(!) "^" means XOR, to reverse.

#  Match all integer numbers

		\d

		[0-9]

#  Match everything other than integer

		\D

#  Match all hex numbers

		\x

		[0-9A-Fa-f]

#  Match everything other than hex

		\X

		[^0-9A-Fa-f]

#  Match all valid word letters

		\w

		[0-9A-Za-z]

#  Match all tabs

		\t

#  Match all spaces

		\s

		\ <- note that there is a space after the backward slash.

	#  Match non-space characters

		\S

	#  Match anything

		\*

	#  Match special characters

		\*

		\.

		\/

		\\

		\[

# Match exact

	\<<match_string>\>
	
	Ex. match "hello" from helloworld.

	/\<hello\>

# Match all trailing space (lines that ends with a space) 

	\s$

	\ $

# Metacharacters for specifying numbers of characters to match

	\+ : to match one or more

# Metacharacters for positions matching

	$  : end of line

	^  : head of line

# Match a word with letters in it being either upper or lower case. 

	/[Jj]ava

# Match and change lower/upper cases

	%s/[Hh]elp/HELP/g

	(!) "s" for "substitute"

	(!) "g" for "global"

# Match between word1 and word2

	<word1>(.*?)<word2>

# One space either exist or not exist

	<word1>\s?<word2>

# One or more space either exist or not exist

	<word1>\s+?<word2>

# Match anything but a whitespace

	(.*?[^ ])

	(!) 
	() means a group
	.*? means anything, non-greedy
	[^ ] means a list, anything but " " -- a white space.

	# Example: find all "+" plus sign without a space at the front and at the back

	[^ ]+[^ ]

# Match { not followed by whitespace

	{[^\s]

	(!) [] means match a character present in the list

	(!) ^\s means not whitespace

# Match if not followed by whitespace

	if[^ ]

