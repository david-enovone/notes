| Version         | 082024.0                 |     |
| --------------- | ------------------------ | --- |
| Candidate Level | Senior Software Engineer |     |
| Knowledge       | Generalist               |     |
| Role            | Individual Contributor   |     |


# Agenda

## 60 minute technical interview

| Mark | Total Time | Topics                                       |
| ---- | ---------- |:-------------------------------------------- |
| 05   | 05 mins | Provide agenda outline; answer any questions |
| 20   | 15 mins | Technical aptitude assessment questions      |
| 50   | 30 mins | Live Coding                                  |
| 60   | 10 mins | Answer candidate questions                   |
|      |            |                                              |
|      | Total: 60  |                                              |

# Technical Aptitude Questions

## Programming

Breadth and depth of programming languages, especially those relevant languages to Company (Python3, Typescript, Postgres)
- Ask for a self assessment:
	- Which languages have you been using lately? For how long?
- Using a scale of one (1) to five (5), one being novice and five being an expert, provide a number for
	- Python3
	- Typescript
	- Postgres
- If candidate provides a 5, ask for clarification. 
	- i.e. Self recognized expert? Peer recognized? Are they an active speaker on the topic? Published author? Blogger / social influencer? 
> 	Sometimes you may not realize it but you may be talking to a core contributor or recognized author, so give the candidate a moment to be their own champion and share.
- Ask about, and understand, the candidates breadth and depth of frameworks: Django, React

## MI & AI
### LLM
Ask about, and understand, the candidates breadth and depth of knowledge creating, building, tuning, and leveraging LLMs. 

**Practical experiences**
- What’s your experience with distributed training for LLMs?
- Describe your experience with frameworks like TensorFlow, PyTorch, or Hugging Face’s Transformers.
- Have you worked with model parallelism or data parallelism? Explain the differences and when to use each.
- Give an example of a successful project where you leveraged an LLM. What were the challenges and how did you overcome them?
- What are the limitations of LLMs, and how do you decide when they are or aren’t the right tool for a task?

**Foundational knowledge**
- Explain the architecture of Transformer models.
	- (optional followup) How are they different than traditional RNNs or LSTMs?
- What are the differences between GPT, BERT, and other Transformer-based models?
	- (optional followup) When would you choose which?

**Building / Training:**
- Describe steps involved in pre-training an LLM from scratch.
- Explain the concept of fine-tuning? Why do we need to fine-tune?
- What's overfitting? How do you handle overfitting when training?

 
## Software Design

Goal is to understand the candidates experience working with Software Design Principles.

Ideal candidates should have some experiences with / knowledge of some of the following prominent Web software design topics:

- SOLID principles
	- Are you familiar with the SOLID principles? If so, what are they? How have you used them in the past?
- Design patterns:
	- Are you familiar with Software Design Patterns? 
	- They're typically labeled as: Creational, Structural, or Behavioral. What is the difference between these?
	- Can you provide a few examples from each?
	- How have you used design patterns in the past?
- Software Development Processes
	- Have you had any experience with:
		- Behavior-driven development (BDD)
		- Domain-driven design (DDD)
		- Feature-driven development (FDD)
		- Test-driven development (TDD)
	- If so, how did it compare to other processes you've used in the past? 
		- How do the processes compare to one another?
- Describe the benefits of a software review process
	- Do you have an example of a particularity tricky review? 
- Have you worked with QA in the past?
	- Describe that experience
	- How did you collaborate with the QA team to ensure adequate testing?
- When was the last time you built automated tests?
	- Was it part of CI/CD pipeline?
	- What benefits did you see from automated testing?


# Live Coding
Note: 
	Big O for both time and space are a must at the completion of the challenge.

> It's not always required that the candidate nail these coding interviews out of the park. 
> What matters most is observing the candidates problem solving, and their ability to articulate their thoughts to you. 
> If necessary, ask the candidate to pretend like they're live streaming their coding session to an audience or class. The audience benefits most when the author narrates their internal dialog. 

Live coding session hosted on LeetCode: https://interview.leetcode.com/interview/
- If the candidate wishes to have an "Open Book" interview (i.e. open up the manual, or heck, even google a bit) ask that they share their screen. 
	- I don't typically "take away points" for this unless the candidate is just copy-pasting solutions they find
- Ask that they refrain from using co-pilot or other code assist AI tools, like ChatGPT

- Pulled from LeetCode pool of questions the following:
	- (easy) [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/description/)
		- This is a bit of "warm up", can be skipped if the candidate was prepped for the LRU cache question in a pre-screen
			- Since it uses a linked list, I've found it primes the brain to recall double-linked lists for the next question.
		- Typically this should take 5 - 10 minutes
			- If it runs over 15 make judgement call to either fill in whatever little piece they're missing, or, just agree to jump ahead 
		- Complexity
			- Time complexity: `O(n)`
			- Space complexity: `O(n)`
	- (medium) [LRU Cache](https://leetcode.com/problems/lru-cache/description/)
		- Two acceptable answers
			1. POD style approach ("built-in") to handle get and put.
			2. Double-linked list
		- Most Senior and above can knock this out in a few minutes, but depending upon how they work and which approach, expect this to take 10 - 15. 
			- If they get stuck this can spiral fast, so course correct if they get too out of bounds
		- Complexity
			- For double-linked list:
			 > Most Engineers have problems with this one, so work it through together. If they miss it.
				- Time complexity: `O(1)` for both `get` and `put`.
				- For `get`:
				    - Check if a key is in a hash map. This costs `O(1)`.
				    - Get a node associated with a key. This costs `O(1)`.
				    - Call `remove` and `add`. Both methods cost `O(1)`.
				- For `put`:
				    - Check if a key is in a hash map. This costs O(1).
				    - If it is, we get a node associated with a key and call `remove`. Both cost `O(1)`.
				    - Create a new node and insert it into the hash map. This costs `O(1)`.
				    - Call `add`. This method costs `O(1)`.
				    - If the capacity is exceeded, we call `remove` and delete from the hash map. Both cost `O(1)`.
				- Space complexity: O(capacity)
			- For built-in:
				- Time complexity: `O(1)` for both get and put.
				- Space complexity: `O(capacity)`
	- (hard) [Smallest Range Covering Elements from K Lists](https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists/description/)
		- If time allows, start this one. Should not be able to finish in time.
			- This can easily take an hour to solve
		- I chose this one as it has over 60% success rate on LeetCode, but still is a subtle tough due to the execution time constraint. 
		- If they get stuck try to nudge them towards an `n*log(m)` solution
		- 20 - 30+ minutes
		- Complexity
			- *simple* Brute Force method (Not acceptable, time limit exceeds)
				- Just a bunch of nested for-loops
				- Time complexity : `O(n3)`.
					- Considering every possible range(element pair) requires `O(n2)` time. 
					- For each range considered, we need to traverse over all the elements of the given lists in the worst case requiring another `O(n)` time. 
					- Here, `n` refers to the total number of elements in the given lists.
				- Space complexity : `O(1)`. Constant extra space is used.
			- *"Better"* Brute Force (Not acceptable, time limit exceeds)
				- Time complexity : `O(n2log(k))`. 
					- The time required to consider every possible range is `O(n2)`. 
					- For every range currently considered, a Binary Search requiring `O(log(k))` time is required. 
					- Here, `n` refers to the total number of elements in the given lists and `k` refers to the average length of each list.
				- Space complexity : `O(1)`. Constant extra space is used.
			- Pointers (Not acceptable, time limit exceeds)
				- Time complexity: `O(n∗m)`. 
					- In the worst case, we need to traverse over `next` array(of length `m`) for all the elements of the given lists.  
					- Here, `n` refers to the total number of elements in all the lists. `m` refers to the total number of lists.
				- Space complexity : `O(m)`. `next` array of size m is used.
			- Using Priority Queue (Acceptable)
				- Time complexity: `O(n∗log(m))`. 
					- Heapification of `m` elements requires `O(log(m))` time. 
					- This step could be done for all the elements of the given lists in the worst case. 
					- Here, `n` refers to the total number of elements in all the lists. `m` refers to the total number of lists.
				- Space complexity: `O(m)`. `next` array of size `m` is used. A Min-Heap with `m` elements is also used.




# Reference

## LLM 
### Foundational
- https://en.wikipedia.org/wiki/Transformer_%28deep_learning_architecture%29
- https://en.wikipedia.org/wiki/BERT_(language_model)
- https://en.wikipedia.org/wiki/Generative_pre-trained_transformer

## SOLID Principles

- **S**ingle-responsibility principle:
  > There should never be more than one reason for a class to change." 
> In other words, every class should have only one responsibility.
- **O**pen–closed principle: 
- "Software entities ... should be open for extension, but closed for modification."
- **L**iskov substitution principle
> "Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it."
- **I**nterface segregation principle
> "Clients should not be forced to depend upon interfaces that they do not use."
- **D**ependency inversion principle
>"Depend upon abstractions, \[not\] concretes."

Reference: 
- https://en.wikipedia.org/wiki/SOLID
- https://www.freecodecamp.org/news/solid-principles-explained-in-plain-english/

## Driven design
- Behavior-driven development (BDD)
	- https://en.wikipedia.org/wiki/Behavior-driven_development
- Domain-driven design (DDD)
	- https://en.wikipedia.org/wiki/Domain-driven_design
- Test-driven development (TDD)
	- https://en.wikipedia.org/wiki/Test-driven_development

## Big O Notation
- Tutorial
	- https://www.geeksforgeeks.org/analysis-algorithms-big-o-analysis/#
- Cheatsheet:
	- https://www.bigocheatsheet.com/
- Full lecture and breakdown
	- https://web.mit.edu/16.070/www/lecture/big_o.pdf
- Wikipedia
	- https://en.wikipedia.org/wiki/Big_O_notation