## Username Generator

Your goal is to write a ruby function that generates a username. It should behave in the following way:

| inputs | output |
|:------|:-------|
| James Bond 2007 | jbond07 |
| John Doe 1978 | jdoe78 |
| John Doe 1978 | jdoe78_1 |
| John Doe 1978 | jdoe78_2 |
| Chico Marx 1887 1 | seller-cmarx87 |
| Harpo Marx 1888 2 | manager-hmarx88 |
| Groucho Marx 1890 3 | admin-gmarx90 |


### Setup
``` bash
git clone THIS_REPO
cd username_generator
```


### Testing

We'll use a tool called `rspec`  to outline our objectives AND test our code as we go... hooray for Test Driven Development (TDD)!

`rspec` is available as a Ruby gem, so start in your terminal by running the command:

``` bash
gem install rspec
```

You might get an error here, but we believe in you. Fix it.

### Test Driven Development -- Red, Green, Refactor.
Take a look inside the `/spec` folder, and you'll see our test suite broken up into 2 files.
- /spec/the_warmup_spec.rb
- /spec/username_spec.rb
>>>>>>> solution

To run the tests for each level, type the following in the command line:

```bash
rspec spec/the_warmup_spec.rb
# or
rspec spec/the_warmup_spec.rb --format documentation
```

You should see the following output:

    FF --> 2 tests failed
    Failures:
      1) #generate_username, level 1 returns the first letter of first_name
         Failure/Error: expect( generate_username("ilias") ).to eq "i"
         ArgumentError:
           wrong number of arguments (1 for 0)
         # ./username.rb:1:in `generate_username'
         # ./spec/username_spec_level_1.rb:8:in `block (2 levels) in <top (required)>'
      2) #generate_username, level 1 lowercases the first letter of first_name
         Failure/Error: expect( generate_username("Ilias") ).to eq "i"
         ArgumentError:
           wrong number of arguments (1 for 0)
         # ./username.rb:1:in `generate_username'
         # ./spec/username_spec_level_1.rb:14:in `block (2 levels) in <top (required)>'

####Hooray!
* The first tests are failing. _We're seeing **RED**._
* Now we need to write code to pass the tests and _turn them **GREEN**_. 
* When all the tests are green, we're ready to _stop and **REFACTOR**_!

**Tips:**

* Run rspec frequently, and test your work.
* BE *VERY CAREFUL* to use the correct function name.


##Challenges
Run: `rspec spec/username_spec.rb`

#### Level 1
Create a function called `format_name` that accepts a user's first_name and last_name and returns a lowercase string that joins the first character of the first_name with the last_name.

Create a function called `format_year` that accepts a four digit integer representing the year (`YYYY`) and parses out the last two digits of the year and returns a a _string_ (`"YY"`).

Create a function called `build_username` that takes a user's first_name, last_name, and birth_year, and returns a string with the following format: it starts with the first letter of the first_name, followed by the last_name, followed by the last two digits of the birth_year.


#### Level 2
Create a function called `check_privilege` that takes a level (integer) and returns the corresponding user_type (string).  
* Allocate privilege using the following table:
    * 0 --> "user" (the default privilege level)
    * 1 --> "seller"
    * 2 --> "manager"
    * 3 --> "admin"

Create a function called `user_type_prefix` that takes a level (integer) and returns the corresponding prefix, e.g. "admin-", "manager-", "seller-". See the tests for more details.

Update your `build_username` function to use prefixes. It should now accept a privilege_level (in addition to the other parameters), and tack it on to the beginning of the username (e.g. "seller-jdoe78"). See the tests for more details.

#### Level 3
Create a function called `generate_username` that has four arguments (first_name, last_name, birth_year, privilege_level) and returns a _unique_ username. Come up with a simple way to store usernames as you create them. 

STRETCH: If a username already exists, append "_1". Then, increment the counter each time you reuse the username (e.g. "jdoe78", "jdoe78\_1", "jdoe7\_2", "bbunny60", "bbunny60\_1").
>>>>>>> solution

#### BONUS -- Command-line inputs
* OPTION 1 -- Interactively get user input from the command line and output a username to the console. I.e. when I run `ruby username.rb` I should be prompted (from the command line) for my name, birth year, etc.
* OPTION 2 -- Accept command line arguments (e.g. `ruby username.rb john doe 1980`) and output a username to the console.

