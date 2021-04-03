# Match from the beginning to the first space -- " "

	regex = "^\S+"

# Count the number of commas -- ","

	regex = ","

	len(re.findall(regex,text))	

# Substitute pattern

	re.sub(sub_what, sub_to_what, input_string)

# Count the number of words (between each space)
	
	regex = "[a-z]+"

# Remove every substring between "=" and "," including the two

	regex = "=(.*?)*,"

	re.sub(regex,"",port_names_raw)	  
