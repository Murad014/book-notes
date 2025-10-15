How Does Duplication Arise?
	1. Imposed duplication - Developers feel they have ne choice - the environment seems to require duplication

	2. Inadvertant duplication - Developers don't realize that they are duplicating information

	3. Impatient duplication - Developers get lazy and duplicate because it seems easier.

	4. Interdeveloper duplication - Multiple people on a team (or on different teams) duplicate a piece of information.


Eliminate Effects Between Unrelated Things.

* Orthogonality means components are independent

* Change one part doesn't require changes in another.

Orthogonality = "no overlap"
If two ideas, skills, or systems are orthogonal, they work separetely without stepping on each other.

So when someone says:
	Keep your system orthogonal
	They mean: "Design it so the parts are independent. Don't mix concerns."

You get two major benefits if you write orthogonal systems: increased productivity and reduced risk.

Grain Productivity
	1. Changes are localized, so development time and testing time are reduced. It's easier to write relatively small, self-contained components than a single large block of code. Simple components can be designed, coded, unit tested, and then forgotten - there is no need to keep changing existsing code as you add new code.

	2. An orthogonal approach also promotes reuse. If components have specific, well-defined responsibilities, they can be combined with new components in ways that were not envisioned by their original implementors. The more loosely coupled your systems the easier they are to reconfigure and reengineer.


Reduce Risk.
An orthogonal approach reduces the risks inherent in any development.
	
	1. Diseased sections of code are isolated. If a module is sick, it's less likely to spread the symptoms around the rest of the system. It's also easier to slice it out and transplant in something new and healthy.

	2. The resulting system is less fragile. Make small changes and fixes to a particular area, and any problems you generate will be restricted to that area.

	3. An orthogonal system will probably be better tested, because it will be easier to design and run tests on its components.

	4. You wil not be as tightly tied to a particular vendor, product or platform, because the interfaces to these third-party components will be isolated to smaller parts of the overall development. 

Coding
	There are several techniques you can use to maintain orthogonality

		1. Keep your code decoupled: Write shy code - modules that don't reveal anything unnecessary to other modules and that don't rely on other modules' implementations. Try the Law of Demeter which we discuss in Decoupling and the Law of Demeter. If you need to change an object's state, get the object to do it for you. This way your code remains isolated from the other code's implementation and increases the chances that you'll remain orthogonal.

		2. Avoid global data: Every time your code references global data, it ties itself into the other components that share that data. Even globals that you intend only to read can lead to trouble(for example, if you suddenly need to change your code to be multithreaded). In general, your code is easier to understand and maintain if you explicity pass any required context into your modules. In object-oriented applications, context is often passed as parameters to objects' constructors.

		3. Avoid similar functions: Often you'll come across a set of functions that all look similar - maybe they share common code at the start and end, but each has a different central algorithm. Duplicate code is a symptom of structural problems. have a look at STRATEGY PATTERN in Design Patterns for a better implementation. 



Tracer Bullets


The tracer code approach has many advantages:

	1. Users get to see something working early. - If you have successfully communicated what you are doing, your users will know they are seeing something immature. They won't be disappointed by a lack of functionality; they'll be estatic to see some visible progress toward their system. They also get to contribute as the project progresses, increasing their buy-in. These same users will likely be the people who'll tell you how close to target each iteration is.

	2. Developers build a structure to work in.  - The most daunting piece of paper is the one with nothing written on it. If you have worked out all the end-to-end interactions of your application, and have embodied them in code, then your team won't need to pull as much out of thin air. This makes everyone more productive, and encourages consistency.

	3. You have an integration platform - As the system is connected end-to-end, you have an environment to which you can add new pieces of code once they have been unit-tested. Rahter than attempting a big-bang integration, you'll be integrating every day(often many times a day). The impact of each new change is more apparent, and the interactions are more limited, so debugginh and testing are faster and more accurate.

	4. You have something to demonstrate. Project sponsors and top brass have a tendency to want to see demos at the most inconvenient times. With tracer code, you'll always have something to show them.

| Feature          | Tracer Code                                   | Prototype                           |
| ---------------- | --------------------------------------------- | ----------------------------------- |
| **Code Quality** | Production-quality, clean                     | Quick & dirty                       |
| **Purpose**      | Build structure for real system               | Explore idea / validate approach    |
| **Lifespan**     | Stays and grows into final product            | Often discarded                     |
| **Architecture** | Uses the **real architecture & tech**         | May skip architecture               |
| **Example**      | First working “login + DB + API” in a new app | Mocked-up UI for testing with users |



Things to Prototype
What sorts of things might you choose to investigate with a prototype? Anything that carries risk. Anything that hasn't been tried before, or that is absolutely critical to the final system. Anything unproven, experimental, or doubtful. Anything you aren't comfortable with. You can prototype.

	1. Architecture.
	2. New functionality in an existing system.
	3. Structure or contents of external data.
	4. Third-party tools or components.
	5. Performance issues.
	6. User interface design

NOTE: PROTOTYPE TO LEARN

How to Use Prototypes
When building a prototype, what details can you ignore?

	Correctness: You may be able to use dummy data where appropriate

	Completeness: The prototype may function only in a very limited sense, perhaps with only one preselected piece of input data and one menu item.

	Robustness: Error checking is likely to be incomplete or missing entirely. If you stray from predefined path, the prototype may crash and burn in a glorious display of pyrotechnics. That's okay.

How Not to Use Prototypes

	Before you embark on any code-base prototyping, make sure that everyone understands that you are writing disposable code. Prototypes can be deceptively attractive to people who don't know that they are just prototypes. You must make it very clear that this code disposable, incomplete, and unable to be completed.


================================================================

Estimating

	Core Idea
		* Estimating is not about 100% accurate.
		* It's about being close enough to guide decisions.
		* With practice, you'll develop an engineer's intuition for size, time, cost, and performance.

	That's why they say:
		Estimate to avoid surprises. 

🔎 Ballpark Estimation — Meaning

A ballpark estimate is a rough, approximate guess about cost, time, or effort.
	•	It’s not exact.
	•	It’s good enough to see the scale of the work.
	•	The idea comes from baseball → if the ball lands somewhere in the ballpark, it’s close enough to count.

👉 In software:
A ballpark estimate tells stakeholders if something is going to take days, weeks, or months — not the exact number of hours.


Where Do Estimates Come From?

	All estimates are based on models of the problem. But before we get too deeply into the techniques of building models, we have to mention a basic estimating trick that always gives good answers: ask someone who's already done it. Before you get too committed to model building, cast around for someone who's been in a similar situation in the past.

--

Estimating Project Schedules.
	This needn't be a paradox if you practice incremental development, repeating the following steps.
		1. Check requirements
		2. Analyze risk
		3. Design, implement, integrate.
		4. Validate with the users.


Tip 19: Iterate the Schedule with the Code.
	“Iterate the schedule with the code” = make your timeline a living, accurate thing driven by real engineering signals and automation. It turns scheduling from guesswork into an ongoing, measurable process that adapts as your codebase (and uncovered realities) evolve.


What to Say When Asked for an Estimate.

You say, "I'll get back to you."

Example

👎 At the coffee machine:
Manager: “How long do you think adding that report feature will take?”
Developer: “Eh, maybe 2 days?”
→ A week later: Manager says “You said 2 days, why isn’t it done yet?”

👍 Better:
Developer: “I can’t really say without looking at the code. I’ll check and get back with a proper estimate.”
→ Now the expectation is managed.



===============================================================================================================================



The Basic Tools.

    Tip 20: Keep knowledge in Plain Text.

    Examples
        ✅ Good (Plain Text)

        Source code (.java, .py, .c)

        Configuration files (.properties, .yml, .json, .ini)

        Documentation (.md, .txt, .rst)

        SQL scripts (.sql)

        Infrastructure as code (.tf, .yaml for Kubernetes)

        ❌ Bad (Opaque/Binary)

        Word docs (.docx) for specs (hard to diff/merge)

        Excel sheets (.xls) for configuration (not transparent, easy to break)

        Proprietary binary formats for data dumps (can’t grep/diff)

        Closed tools where knowledge lives only in a GUI (no text to store in Git)


The Power of Test
    Since larger and slower aren't the most frequently requested features from users, why bother with plain text? Whar are the benefits?

    1. Insurance against absolescence.
    2. Leverage.
    3. Easier testing.


Shell Games
	* If you do all work using GUIs, you are missing out on the full capabilities of your environment. You won't be able to automate common tasks, or use the full power of the tools avaulable to you. And you won't be able to combine your tools to create customized macro tools. A benefit of GUIs is WYSIWYG - what you see is what you get. The disadvantages is WYSIAYG - what you see is all you get.

TIP 21
	Use the Power of Command Shells.



Debugging Strategies
	NOTE:
		Bug Reproduction
			No, our bugs aren't really multiplying (although some of them are probably old enough to do it legally). We're talking about a different kind of reproduction.
			The best way to start fixing a bug is to make it reproducible. After all, if you can't reproduce it, how will you know if it is ever fixed?
			But we want more than a bug that can be reproduced by following some long series of steps; we want a bug that can be reproduced with a single command. It's a lot harder to fuix a bug if you have to go through 15 steps to get to the point where the bug shows up.

=========================================================================================================================================================

PRAGMATIC PARANOIA.
 Tip 30 - You can't write PERFECT SOFTWARE.

If there's any doubt, we validate all information we're given. We use assertions to detect bad data. We check for consistency, put constraints on database columns, and generally feel pretty good about ourselves. 
	BUT PRAGMATIC PROGRAMMERS TAKE THIS A STEP FURTHER. THEY DON'T TRUST THEMSELVES, EITHER. Knowing that no one writes PERFECT CODE, including themselves, Pragmatic Programmers code in defenses against their own mistakes. We describe the first defensive measure in Design by Contract: clients and suppliers must agree on rights and responsibilities.

1.	Notes - Dead Programs Tell No Lies.
		* Principle: Fail fast - stop program when error occur instead of continuing in an invalid state.
		* Reason: A crash is visible and contained; silent bugs cause data corruption, security risks, hidden failures.
		* Practices: 
			* Validate inputs & invariants.
			* Throw exception on unexpected conditions. 
			* Log errors clearly before termination
			* Use rollback/recovery mechanisms (e.g DB transactions)

		* Mindset: Better no result than a wrong result.

2. Assertive Programming - describes an easy method of checking along the way - write code that actively verifies your assumptions.
	Assertive Programming = don't just assume your code is correct - make your codde check its own assumpltions as it runs.
	For example: 
		* If you assume a list is never empty -> assert it
	This way, if reality doesn't match your assumptions, the program fails immediately instead of quietly producing wrong result.


	Notes for your Notebook
		* Assertive Programming = check assumptions explicity with assertions.
		* Purpose: catch bugs early, fail fast, self-documented expectations.
		* Use for: preconditions, postconditions, invariants
		* Don't assume -> assert!

----------------------------------------------------------------------------------------------------------------------

When everybody actually is out to get you, paranoia is just good thinking
														-> Woody Allen

What does it mean? 
If danger is real, caution isn't paranoia - it's smart thinking.
	We have learned:
		1. Don't trust your code, your assumptions, or even your own inputs.
		2. If bugs, bad data, and user mistakes will happen, then being "paranoid" - adding checks, assertions, and defensive code - isn't crazy. IT'S JUST GOOD ENGINEERING.

===============================================================================================================================================================

																					DESIGN BY CONTRACT
													Nothing astonishes men so much as common sense and plain dealing. - Ralph Waldo Emerson

One of the best solutions for ensuring plain dealing is the CONTRACT - A Contract defines your rights and responsibilities, as well as those of the other party. 

DbC is commong sense formalized:
	* DbC is common sense formalized:
		* Caller promises preconditions (e.g amount > 0).
		* Method promises postconditions (e.g balance increases).
		* System enforces invariants (e.g total debits == total credits).
	* This "plain dealing" is just being explicit about what's expected and what's guaranteed.
	* Instead of "trust me, it works," DbC is like a contract you can't ignore.

Example:
	Without contract
```
public void withdraw(Account account, double amount) {
    // assumes account is valid, amount positive, and enough balance...
    account.setBalance(account.getBalance() - amount);
}
```

With Design by Contract 

```
public void withdraw(Account account, double amount) {
    assert account != null : "Account must not be null";
    assert amount > 0 : "Amount must be positive";
    assert account.getBalance() >= amount : "Insufficient funds";

    double oldBalance = account.getBalance();
    account.setBalance(oldBalance - amount);

    assert account.getBalance() == oldBalance - amount : "Postcondition failed";
}
```

================================================================================================

			Loop Invariants

A loop invariant is a logical statement that is always true:
	* Before the loop starts.
	* During every iteration of the loop.
	* When the loop ends.

It's like a mini contract for your loop - describing what must always hold ture, even while the loop is in progress.

Example: Finding the Maximum in an Array.

```
int m = arr[0];      // assume arr.length > 0
int i = 1;

// Loop invariant: m = max(arr[0 : i-1])
while (i < arr.length) {
    m = Math.max(m, arr[i]);
    i = i + 1;
}
```

1. Before loop starts:
	* m = arr[0];
	* i = 1
	* INVARIANT says: "m" is the max of all elements from arr[0] up to i.
	* So m = max(arr[0:0]) => TRUE

------------------------------------------------------------------------------------------------

												SEMANTIC INVARIANTS
1. They Are fundamental truths about a system - rules that must never be broken unders any circumstances.
2. They act like PHILOSOPHICAL CONTRACTS: higher-level guarantees that guide design decisions.
3. They differ from business policies (which can change), because semantic invariants are permanent and central to the meaning of the system.

Example: Debit Card Transaction System.
	1. Requirement: A user must never be charged twice for the same transaction.
	2. Why? Because duplicate charges would break trust and create financial harm.
	3. So, the system is designed with this invariant in mind

Difference Between Policy and Semantic Invariant
1. Policy: Rules that can change(ATM withdrawals are limited to 500 dollar in a day - management can update this.
2. Semantic Invariant: Rules that must always hold.


Tip 35: Finish What You Start.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
																	BEND, OR BREAK
In Reversibility, we talked about the perils of irreversible decisions. In this chapter, we'll tell you how to make reversible decisions. In this chapter, we'll tell tou how to make reversible decisions, so your code can stay flexible and adaptable in the face of an uncertain world.

First we need to look at coupling - the dependencies among modules of code. In decoupling and the Law of Demeter we'll show how to keep separate concepts separate, and decrease coupling.

A key concept in creating flexible code is the separation of a data model from a view, or presentation, of that model. We'll decouple models fron views in It's Just A View.

Finally, there’s a technique for decoupling modules even further by providing a meeting place where modules can exchange data anonymously and asynchronously. This is the topic of Blackboards.
Armed with these techniques, you can write code that will “roll with the punches.”


```
The Law of Demeter, also known as the principle of least knowledge, is a software design guideline that states an object should only communicate with its immediate "friends" and not with "strangers". This means an object should only call methods on itself, objects passed in as arguments, any objects it creates, or its direct component objects. The core idea is to reduce coupling between classes, making code easier to test, refactor, and maintain. 
```

--------------------------------------------------------------------------------------------------------------------------------------------

																			Decoupling and the Law of Demeter.
Good fences make good neighbors.

In Orthogonality, page 34, and Design By Contract, page 109, we suggested that writting "shy" code is beneficial. But "shy" works two ways: 
	1. Don't reveal yourself to others
	2. Don't interact with too many people.

-----

The Law Of Demeter for Functions

The Law of Demeter for functions attempts to minimize coupling between modules in any given program. It tries to prevent you from reaching into an object to gain access to a third objecct's methods.
By writing "shy" code that honors the Law Of Demeter as much as possible, we can achieve our objective:
	
	Tip 36: Minimize Coupling Between Modules

====================================================================================================================
																Metadata-Driven Applications
Put Abstractions in Code, Details in Metadata.

There are several benefits to this approach:
	1. It forces you to decouple your design, which results in a more flexible and adaptable program.
	2. It forces you to create a more robust, abstract design be deferring details - deferring them all the way out of the program.
	3. You can customize the application without recompiling it. You can also use this level of customization to provide easy work-arounds for critical bugs in live production systems.
	4. You may even be able to implement several differen projects using the same application engine, but with different metadata.


DON'T WRITE DODO-CODE
Without metadata, your code is not as adaptable or flexible as it could be. Is this a bad thing? Well, out here in the real world, species that don't adapt die. 

The dodo didn't adapt to the presence of humans and their livestock on the island of Mauritius, and quickly became extinct. It was the first documented extinction of a species at the hand of man.
DON'T LET YOUR PROJECT (OR YOUR CAREER) GO THE WAY OF THE DODO.
