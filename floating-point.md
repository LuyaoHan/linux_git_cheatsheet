Same values executed in different orders gets you different values.
IEEE 754 Single Precision:
- Unnormalized number: value smaller than the smallest fraction will be represented as unnormalied. (0.00001010)

	(-1)**sign * mantissa * (1 - exponent)

- Normalized number: large value: 1.1011 * 10**23
	(-1) ** sign * 1.mantessa * (exponent - 127)

- Trap: Float point comparison 0.01 == 0.01 is not accurate, must do 
fabs(0.01-0.01) < some limit

- Trap: 0.1 + 0.1 + 0.1 ... after many iterations big differece accumulates after many loops

- Trouble in embedded systems:
	- NaN involved in comparison
	- if (currentSpeed > maxSpeed) {
		shutDown();
	}

	but if currentSpeed is NaN --> it will return false, which is incorrect.
	- Nan == Nan also returns false which is incorrect, so should use isnan();
- Infinity > maxSpeed --> will return true correctly

- Infinity --> you got infinity when you divide a number by 0.

- Best Practices for floating point:
	- scaled integer, count 1/10 of a seconds in integer
	- Binary Coded Decimal + radic point 
	- Fixed Point (use normal point addition of CPU) and move back the floating point. Just like you did it in middle schoo.

- Hard to handle special values:
	- NaN is especially tricky to get right
		- NaN is a special number
		- Roundoff errors

- Manage and handle roundoff error
	- Double floating point to work with (less roundoff error but still there)
	- avoid doing floating point in iterative loops.
	
