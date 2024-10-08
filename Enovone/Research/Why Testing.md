## Testing Sucks
- It seems like a waste of time
- It takes up time that could be spent writing features
- It takes up time that could be spent elsewhere
- It waste time writing tests for something we may not even keep
- The code changes which means the tests have to be updated which is a waste of time
- Fixing tests means I'm slower to release
- Having to learn new testing framework is something extra that isn't working on new features
- If I test my work before I ship it, why would I need automated tests?
- Devs should be trusted to write good code that doesn't break



## Value of Testing
- Saves time
	- Automated tests run anytime you'd like, in parallel, beyond human speed
- No Human
	- Humans make errors and mistakes -- coded automated tests always execute as they're programmed
	- No errors in checking for errors
- Lower costs
	- Lowers the cost of testing/QA work
	- Lowers the cost of maintenance of the code (less bugs get to prod)

### Value for small teams
- No time to test
	- If we have limited time already, then the value we get out of adding additional testing has exponential return value
- High risk
	- as a small team startup, we're risking a lot already - adding in the risk of zero or no test coverage only adds to that risk
- Dev time is valuable 
	- Developer time is valuable, so we should get the most value from that time -- instead of hunting down weird edgecases or trying to discover why product is having trouble with one thing or another -- developers can focus on making new features, not on debugging or fixing problems
		- Each time a developer is pulled away from their work to assist with a bug costs more than just writing a test to prevent it from occuring in the first place
- The TDD paradigm forces us to write code different
	- Writing testable code forces us to write smaller, more concise, testable code.
	- This increases the value of our code in the long term
	- This means if we pivot, we'll need to touch less massive functions and instead only update the functions that need it
	- And we'll have tests to show that the pivot worked and we can push to prod without worrying / testing everything from scratch

