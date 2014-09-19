## An ideal browser testing framework

Just a list of ideas I have in mind for the perfect testing framework
(for UI testing - for unit tests, mocha / some simple assert
library is just fine)

### Testing DSL reminiscent of English (à la Gherkin)

- Maybe without "Given/Then/When/And", though

### Come with a reasonable set of commonly used steps

- "I click button 'Hello'"
- "I go to page '/login'"
- "I input 'Antti' in form field 'Name'"
- etc.

### Simple command line UI

To all scenarios / features matching 'some description here'

	$ test some description here

To run interactively the scenario 'adding a new user':

	$ test -i adding a new user

### It should show you the step it is currently trying to do

	$ test invalid password
	Feature "logging in", scenario "invalid password".
	Running: (login.feature:48) "I enter 'bob' into text input 'user'"
	Running: (login.feature:49) "I enter 'invalid' into text input 'password'"
	Running: (login.feature:50) "I click button 'log in'"
	Running: (login.feature:51) "I see error notification"

### It should allow you to to step through the tests manually, too

	Feature "logging in", scenario "invalid password".
	Next step: (login.feature:50) "I click button 'log in'"
	> <enter>
	[Find button with 'log in'... found. -> $1] [Click button $1... ok.]
	Next step: (login.feature:51) "I see error notification"
	> 

### Fail fast: undefined steps should be shown immediately

	$ test invalid password
	Feature "logging in", scenario "invalid password".
	Undefined step in login.feature:51: "I see error notification" 
	$ 

