# yesno
8 lines answers any question consistently with this one simple Procedural Generation trick

# Example (quotes are required)

./yesno "Am I cute?"

  Yes
  
./yesno "Is this clever?"

  No
  
./yesno "Pineapple on pizza?"

  No
  
# Explanation

Aside of handling input, this code does almost nothing!

This is the minimum effort possible to arrive at a random but consistent response to arbitrary input: Using the input as part of seeding the Pseudo Random Number Generator (PRNG). To do this, the user input is 1) converted to lowercase 2) base64 encoded and 3) converted to an integer that can be fed to random.seed. 

  random.seed(int.from_bytes(base64.b64encode(sys.argv[1].lower().encode()), byteorder='big'))

Once seeded with value X, Python's PRNG will generate the same "random" values in the same order.
That means the same input string will produce the same answer, everytime, forever. Kinda cool huh.

PS: Rather than bothering with "if" statements, a coin is just flipped to choose an answer from the "aNswers" array. ;)

  aNswers = ["Yes", "No"];
  
  (...)
  
  print (aNswers[random.randint(0,1)])

# Disclaimer
I like pineapple on pizza.
