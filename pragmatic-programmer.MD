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



============================================================================================================================================

---

### 🧩 1. **What people *think* coding is**

The book says:

> “Conventional wisdom says that once a project is in the coding phase, the work is mostly mechanical…”

That means many people (especially managers or beginners) **believe coding is just typing** — taking a design document and translating it into code like a robot.
They think once design is done, programmers just follow instructions.

💬 Example of that mindset:

> “We already designed it. Just go code it up!”
> (as if the programmer’s job is mechanical work, not thinking work)

---

### ⚠️ 2. **But in reality — coding requires constant thinking**

The authors argue:

> “Coding is not mechanical.”

Every line of code involves **choices**:

* Which data structure is best?
* Is this logic clean and readable?
* What happens if the input is invalid?
* Is this algorithm efficient?
* What if I need to change this later?

So, a good programmer is always **analyzing, questioning, and improving** — not just typing.

---

### 💥 3. **“Programming by coincidence”**

They warn:

> “Developers who don’t actively think about their code are programming by coincidence.”

That means:

* You write code that “just happens” to work — but you don’t really understand *why*.
* If it breaks tomorrow, you won’t know how to fix it.
* You rely on luck instead of logic.

💡 **Example:**

```java
if (someList.size() > 1) {
    process(someList.get(1));
}
```

It might “work,” but you don’t stop to ask:
— What if the list is empty?
— Why index 1, not 0?
— Could there be concurrency issues?

That’s *programming by coincidence.*

---

### 🚦 4. **Be intentional and critical**

> “Pragmatic Programmers think critically about all code, including our own.”

You don’t just accept code because it “works.” You ask:

* Is this the simplest solution?
* Is it maintainable?
* Is it testable?
* Is it clear to others?

That’s what it means to **code consciously**, not mechanically.

---

### 🧠 5. **Testing, refactoring, and performance**

They mention other key ideas:

* **Algorithm Speed** → Think about performance before it’s a problem.
* **Refactoring** → Keep improving existing code.
* **Code That’s Easy to Test** → Write code in a way that makes testing simple.
* **Evil Wizards** → Be careful with auto-generated code (don’t trust magic tools unless you understand them).

---

### 🚗 6. **Car-driving analogy**

> “Good, safe drivers are constantly reviewing the situation…”

Just like driving:

* Most of the time, you’re doing normal stuff (coding routines).
* But a good driver keeps an eye out for *potential dangers* — traffic, pedestrians, sudden changes.
* Similarly, a good programmer keeps thinking, checking assumptions, and watching for problems.

So — **don’t code on autopilot.**
Always stay aware, deliberate, and thoughtful.

---

### ✅ **In summary**

| Wrong Mindset                               | Pragmatic Mindset                                      |
| ------------------------------------------- | ------------------------------------------------------ |
| “Coding is just typing what’s designed.”    | “Coding is continuous design and decision-making.”     |
| “If it works, it’s fine.”                   | “If it’s clear, maintainable, and correct, it’s fine.” |
| “I’ll fix it later.”                        | “I understand *why* it works and how to improve it.”   |
| “The tool generated it — I don’t care how.” | “I must understand the code, even if it’s generated.”  |

---

Would you like me to show you a **Java example of “programming by coincidence” vs. “programming with intent”**?
It’ll make this lesson super clear.


Perfect, buddy 👇 let’s see what **“Programming by coincidence” vs “Programming with intent”** looks like in real Java code.

---

## 🧱 Example Scenario

Let’s say you’re writing a small method to **calculate a user’s discount** based on how much they spent.

---

### ❌ **Programming by Coincidence**

```java
public double calculateDiscount(double total) {
    double discount = 0;
    
    if (total > 100) {
        discount = total * 0.1;  // 10% discount
    } else if (total > 50) {
        discount = 5; // fixed discount
    }
    
    return discount;
}
```

#### 🚩 What’s wrong here?

At first glance, it “works”… but let’s think:

* What if `total` is negative? (bug)
* Why 5? Why 100? — there’s no reasoning or documentation.
* What happens if the company changes discount rules?
* What if we later need to apply customer-level discounts (VIPs)?
* What if floating-point rounding matters?

👉 This is **“programming by coincidence.”**
It works *by luck*, not by clear understanding or design.

---

### ✅ **Programming with Intent**

Let’s write the same logic consciously, with reasoning and flexibility.

```java
public class DiscountPolicy {
    private static final double VIP_DISCOUNT_RATE = 0.15;
    private static final double STANDARD_DISCOUNT_RATE = 0.10;
    private static final double SMALL_DISCOUNT_AMOUNT = 5.0;
    
    public double calculateDiscount(double total, boolean isVip) {
        if (total < 0) {
            throw new IllegalArgumentException("Total cannot be negative");
        }

        if (isVip) {
            return total * VIP_DISCOUNT_RATE;
        }

        if (total > 100) {
            return total * STANDARD_DISCOUNT_RATE;
        }

        if (total > 50) {
            return SMALL_DISCOUNT_AMOUNT;
        }

        return 0;
    }
}
```

#### 💡 Why is this “intentional programming”?

* ✅ Clear **constants** explain the logic (no “magic numbers”).
* ✅ Edge cases are handled (negative total).
* ✅ Easy to change discount rules — no need to touch business logic.
* ✅ Self-documenting: the method’s intent is obvious.
* ✅ Easy to test — deterministic output.

---

### 🧠 How a Pragmatic Programmer Thinks

While writing this, you’re asking:

* “What are the possible inputs?”
* “Will this logic still make sense in 6 months?”
* “How can I make this readable to others?”
* “Can I test it easily?”
* “If rules change, where will I update it?”

That mindset turns you from a **coder** into a **software craftsman.**

---

### 🚀 Quick Summary

| Concept     | By Coincidence            | With Intent                        |
| ----------- | ------------------------- | ---------------------------------- |
| Mindset     | “It works, who cares why” | “I understand *why* it works”      |
| Flexibility | Hard-coded rules          | Configurable constants or metadata |
| Testing     | Hard to test              | Simple, predictable                |
| Maintenance | Fragile                   | Easy to adapt                      |
| Confidence  | Low                       | High                               |

---

Would you like me to extend this example to show how **business rules could be moved to metadata/config (JSON or YAML)** — like the next section *“Put Abstractions in Code, Details in Metadata”* talks about?
That would connect both ideas together perfectly.




TIP 44: Don’t Program by Coincidence

=====================================================



Excellent 👏 — this section, **“How to Program Deliberately,”** is one of the *core philosophies* of *The Pragmatic Programmer*.

Let’s break it down so you can **learn fast and deeply**, with simple explanations and real-world developer mindset 🧠👇

---

## 🧩 The Main Idea

**Don’t write code accidentally — write it intentionally.**

That means:

> You always know *why* something works, *how* it works, and *what* might break it.

When you don’t — you’re programming “by coincidence.”

---

## ⚡ Let’s Decode Each Rule Quickly

### 1. **Be aware of what you’re doing**

> Don’t drift into messy situations like a frog in warm water — small bad habits will boil you slowly.

🧠 Example:
You start hardcoding some values *“just for now”*, skip one small validation, don’t fix one warning…
→ Over time, your project becomes a pile of problems.

✅ Always ask yourself:

* Why am I writing this code?
* Does this line belong here?
* Is there a simpler or cleaner way?

---

### 2. **Don’t code blindfolded**

> Never use a tool, library, or API you don’t understand.

🧠 Example:
You copy a StackOverflow answer using `@Transactional(propagation = REQUIRES_NEW)` but don’t know what it does.
It “works”… until you break all your database consistency. 😬

✅ Learn first, *then* use.

---

### 3. **Proceed from a plan**

> Always have a small plan — even if it’s just in your head.

🧠 Example:
Before coding, know:

* What is the goal?
* What are the inputs and outputs?
* What’s the success condition?

✅ Plan prevents chaos.

---

### 4. **Rely only on reliable things**

> Don’t build on top of guesses, coincidences, or lucky outcomes.

🧠 Example:
Your code only works when you restart twice?
Or it “sometimes” passes tests?
That’s not reliability — that’s luck.

✅ Fix root causes, don’t accept “it just works somehow.”

---

### 5. **Document your assumptions**

> If your code assumes something, write it down.

🧠 Example:
You think `user.getName()` is never null — prove it:

```java
assert user.getName() != null : "User name should not be null";
```

✅ These small checks save hours of debugging later.

---

### 6. **Test assumptions, not just code**

> Verify what you *believe* to be true.

🧠 Example:
If you think your function always returns sorted data — test it:

```java
List<Integer> result = service.getIds();
assertTrue(isSorted(result));
```

✅ Assertions = live documentation + protection.

---

### 7. **Prioritize effort**

> Focus on important, hard things — infrastructure, core logic.

🧠 Example:
Don’t spend 5 hours making your loading spinner look pretty when your API isn’t stable yet.

✅ Do the tough, critical things first.

---

### 8. **Don’t be a slave to history**

> Old code is not sacred. Refactor or replace when needed.

🧠 Example:
“This function has always been here” is not a reason to keep it.
If it’s ugly, slow, or confusing → fix it.

✅ Code evolves, or it dies.

---

### 9. **When something works but you don’t know why...**

> Stop. Investigate.
> If you don’t understand *why* it works, it might break tomorrow.

🧠 Example:
If removing a `Thread.sleep(1000)` breaks your code — that’s a red flag. It’s hiding a timing problem.

✅ Know the reason behind every behavior.

---

## 🎯 In short

| Rule                        | Mindset                |
| --------------------------- | ---------------------- |
| Always aware                | Stay conscious         |
| Don’t code blindfolded      | Learn your tools       |
| Plan before code            | Structure your thought |
| Rely on reliable things     | Avoid luck             |
| Document assumptions        | Be explicit            |
| Test assumptions            | Verify beliefs         |
| Prioritize effort           | Focus on impact        |
| Don’t be a slave to history | Refactor freely        |
| Don’t trust coincidences    | Understand everything  |

---

### 🧠 One-Sentence Summary:

> **“Deliberate programming” means: every line of your code exists for a clear, known reason — never by chance.**

---

Would you like me to show how this looks in a **real code example** — like the “blindfolded vs deliberate” approach in a Spring Boot service method?
It’ll help you *see* this philosophy in practice.

=========================================================================================================================================================


That’s a **classic excerpt** from *The Pragmatic Programmer* — the “Refactoring” section. 🌱

Let’s break it down together 👇

---

### 💡 **Main Idea**

The authors (Andrew Hunt & David Thomas) argue that **software development is not like building construction** — it’s more like **gardening**.
Software isn’t something you build once and forget about. It grows, changes, and needs **constant care and refactoring** to stay healthy.

---

### 🏗️ **Why the “construction” metaphor fails**

In traditional building construction:

1. Architects design everything up front (blueprints).
2. Builders just follow the plan step by step.
3. Once the building is complete, it rarely changes.

But in **software**, requirements evolve, technologies shift, and design decisions need to adapt.
Unlike a building, software doesn’t remain static — it *lives* and *changes.*

---

### 🌿 **Why “gardening” fits better**

A garden:

* Starts with a plan but grows unpredictably.
* Needs pruning, replanting, fertilizing, and weeding.
* Requires ongoing care and small adjustments over time.

Similarly, software:

* Needs **refactoring** (pruning and reorganizing code).
* May require removing “weeds” (bad patterns, dead code).
* Grows organically as new features are added.
* Needs continuous attention to stay maintainable and elegant.

---

### 🧩 **What is Refactoring**

> **Refactoring** = the process of improving the design, structure, and readability of code *without changing its behavior.*

It means:

* Splitting large methods into smaller ones.
* Renaming confusing variables.
* Simplifying logic.
* Removing duplication.
* Reorganizing modules for clarity.

It’s *not rewriting the whole thing*, but carefully reshaping it so that the software remains healthy and adaptable.

---

### 🧠 **Pragmatic takeaway**

Refactoring isn’t failure — it’s **a natural and necessary part of growth**.
Just as gardeners continuously shape their gardens, developers continuously shape their codebase.

> “Code needs to evolve; it’s not a static thing.”

---

Would you like me to give you a **short modern summary** of this idea (like a paragraph you could quote in an essay or interview)?

Excellent — this is another *Pragmatic Programmer* gem, and it’s the perfect continuation of the previous passage. Let’s unpack it clearly 👇

---

## 💡 **Main Idea**

Refactoring is **not optional** — it’s **a responsibility**.
The authors warn that skipping refactoring because of “time pressure” is a **false economy**.
If you delay cleaning up bad code now, you’ll pay a much **higher price** later when the system becomes larger and harder to change.

---

## 🧱 **The Real-World Problem**

You tell your boss:

> “The code works, but I need another week to refactor it.”

Their likely response:

> “We don’t have time for that. Just ship it.”

That’s the **real-world tension**: developers understand the technical debt; managers focus on deadlines. But, as the authors point out, **ignoring refactoring under time pressure is shortsighted** — you’re just pushing the pain into the future, when it’ll be *more expensive* and *riskier* to fix.

---

## 🩺 **The Medical Analogy**

Think of messy code as a **growth** in the body:

* If you remove it early, it’s minor surgery.
* If you ignore it, it grows and spreads — and removing it later is *far more dangerous*.
* Wait too long, and the **entire system might die** (i.e., the codebase becomes unmaintainable).

It’s a vivid metaphor — and it perfectly captures the idea of **technical debt compounding over time**.

---

## ⚙️ **Tip 47 — Refactor Early, Refactor Often**

This is the practical rule the authors give:

* 🔁 Don’t wait for a “big refactoring day.”
* 📝 Keep a running list of parts that need refactoring.
* ⏰ Schedule them — treat refactoring as real work, not a luxury.
* 📢 Communicate — let your team and users know what’s being refactored and when.

---

## 🧠 **Modern Summary**

Refactoring is preventive maintenance for your codebase.
If you postpone it to save time now, you’ll pay for it with interest later — in bugs, complexity, and frustration.
Refactor continuously, not just when things break.

> **Refactor early, refactor often — or you’ll eventually refactor in panic.**

---

Would you like me to summarize this *Real-World Complications* section in **one short paragraph** (e.g., something you could memorize or use in a talk/interview)?

========================================================================================================================================================================

Perfect — you’ve reached one of the most *practical* and *famous* sections of **The Pragmatic Programmer**: *How to Refactor*.
Let’s go through it step by step so you learn it fast and deeply 👇

---

## 🧠 What Refactoring Really Means

Refactoring = **redesigning code without changing what it does**.
It’s about **improving structure**, **removing duplication**, and **making code easier to maintain** — *while keeping behavior the same*.

The authors remind you that refactoring started in the **Smalltalk** world (where tools and class browsers made it easy) — and later became popular thanks to **Martin Fowler’s book *Refactoring* (1999)**.

But they also warn:

> Refactoring is not chaos. Don’t rip up code “with wild abandon.”
> Do it **slowly, deliberately, and carefully**.

---

## ⚙️ Martin Fowler’s 3 Core Rules for Safe Refactoring

### 1️⃣ Don’t refactor *and* add features at the same time

When you refactor, focus only on improving structure — no new functionality.
Mixing the two will confuse your goal and make debugging harder.

### 2️⃣ Have good tests — and run them constantly

Before refactoring, you must have **reliable regression tests**.
Each time you change the code, **run the tests immediately**.
That way, if something breaks, you’ll know exactly what caused it.

> 🧩 **Tests give you courage to refactor.** Without them, you’re walking blind.

### 3️⃣ Take small, deliberate steps

Don’t rewrite everything at once.
Instead, make *tiny* safe changes — e.g.

* move one field between classes,
* merge two similar methods,
* rename a variable.

After *each* change → run the tests.
This step-by-step approach avoids long debugging sessions.

---

## 🧰 Automatic Refactoring Tools (Then & Now)

At the time the book was written (1999), refactoring tools were only in **Smalltalk**.
Now, every modern IDE (IntelliJ, Eclipse, VS Code, etc.) has:

* Rename refactorings
* Extract method/class
* Move/inline methods
* Change signatures safely
  These are the “refactoring browsers” the authors predicted — and they were right!

---

## 💣 Handling Big Changes

When you make **drastic refactors** (like changing a module’s interface):

* Intentionally **break the build** so that dependent code fails to compile.
* This forces you to find and update all the affected parts immediately.
  That’s how you avoid hidden mismatches between old and new code.

---

## 🧩 Final Message

> “If it hurts now, but will hurt even more later — fix it now.”
>
> Don’t live with broken windows. Clean as you go.
> Refactor both the problem and the code that depends on it.

---

## 🧠 Quick Summary to Memorize

> **Refactor deliberately:**
>
> * Don’t mix with new features
> * Have strong tests
> * Take small, safe steps
>
> **Refactor early, refactor often — never live with broken windows.**

---

Would you like me to give you a **short practical guide** — like a checklist you can use in your real coding workflow to know *when* and *how* to refactor safely (with examples)?

======================================================================================================================================================================



Excellent — this section, **“Digging for Requirements,”** is one of the most insightful parts of *The Pragmatic Programmer*. It teaches how to **separate true requirements** from **policies, assumptions, and implementation details**, and how to truly **understand users**.

Let’s unpack it step by step 👇

---

## 🧱 **1. What Is a True Requirement?**

The book starts by asking:

> “How can you recognize a true requirement while you’re digging through all the surrounding dirt?”

### ✅ A **requirement** is:

> Something that **must be accomplished** by the system.

Example of *clear requirements*:

* “An employee record may be viewed only by a nominated group of people.”
* “The cylinder-head temperature must not exceed the critical value.”
* “The editor will highlight keywords depending on file type.”

👉 These are **goals or conditions** that the system must satisfy — not specific ways to achieve them.

---

## ⚙️ **2. Why Requirements Are Hard**

Because **people don’t usually express real requirements clearly**.
They mix in:

* **Current business policies**
* **Implementation ideas**
* **Personal habits**

Let’s look at the example from the book:

### ❌ User says:

> “Only an employee’s supervisors and the personnel department may view that employee’s records.”

### ✅ Better requirement:

> “Only authorized users may view an employee’s record.”

---

## 🔍 **3. Difference Between Requirement and Policy**

| Concept            | Meaning                    | Example                                     | Problem if Mixed Up       |
| ------------------ | -------------------------- | ------------------------------------------- | ------------------------- |
| **Requirement**    | What must happen           | “Only authorized users may view records.”   | Flexible and future-proof |
| **Policy**         | How it happens *today*     | “Only supervisors and HR can view records.” | Changes frequently        |
| **Implementation** | How the system enforces it | e.g., Access control code or metadata       | Should be adaptable       |

### 💡 The Key Insight:

If you code the *policy* instead of the *requirement*, you’ll have to **rewrite the program every time the policy changes**.
But if you design based on *requirement*, you can just **update configuration or metadata**.

---

## 🪞 **4. User Interface Example**

### ❌ User says:

> “We need a list box to select the loan term.”

This might sound like a requirement, but it’s often not.
Ask:

* Do they really *need* a **list box**?
* Or do they just need a **way to select** the loan term?

### ✅ True requirement:

> “The system must let the user choose a loan term.”

Now developers can decide *how* to implement that — a list box, dropdown, voice input, etc.

---

## 💬 **5. Find the Real Reason Behind User Actions**

> “It’s important to discover the underlying reason why users do a particular thing, rather than just the way they currently do it.”

Users often describe **their current process**, not **their real need**.
Your job is to find the **why** behind the **what**.

Example:

* User: “We print reports every morning.”
* Real reason: “We need to know daily inventory levels.”
  → Maybe you can build a dashboard instead of a printed report.

✅ **You’re solving business problems, not reproducing old habits.**

---

## 🧍‍♂️ **6. Become a User Yourself**

The authors give brilliant advice:

> “Become a user.”

That means:

* If you’re building a system for customer support → sit with the help desk.
* Building stock management → work in the warehouse for a few days.

This helps you:

* Understand **real workflow**
* Build **trust** with users
* Gather **true insights** that users might never articulate

⚠️ Just don’t interfere — observe and learn.

---

## 🧠 **7. Tip 52 — Work with a User to Think Like a User**

> “The requirements mining process is also the time to build a rapport with your user base.”

* You’re not just collecting requirements.
* You’re **building relationships and trust**.
* This makes users more honest, more open, and more cooperative later.

---

## 🧩 **8. Summary of Lessons**

| Lesson                                           | Meaning                                                               |
| ------------------------------------------------ | --------------------------------------------------------------------- |
| **True requirements ≠ user statements**          | Dig deeper — users often describe current practice, not actual needs. |
| **Separate requirement, policy, implementation** | Keeps your system flexible and maintainable.                          |
| **Don’t hardcode business rules**                | Put policies in metadata/configuration instead.                       |
| **Understand the “why” behind requests**         | Solve business problems, not habits.                                  |
| **Work with users directly**                     | You’ll build empathy, trust, and insight.                             |

---

## ⚡ Example in Practice

Imagine you’re building an HR system.

### User says:

> “Supervisors and HR can see employee salaries.”

### If you code it directly:

```java
if(user.role.equals("SUPERVISOR") || user.role.equals("HR")) {
   showSalary();
}
```

When company policy changes (“Finance can also see salaries”), you must **change the code**.

### But if you abstract it:

```java
if(user.isAuthorized("VIEW_SALARY")) {
   showSalary();
}
```

Now you just update **metadata or configuration**, not your code.

That’s **the power of separating requirement from policy**.

---

## 🏁 **Bottom Line**

> **Good developers don’t just listen — they interpret.**

To “dig for requirements” means:

* Don’t take user statements at face value.
* Find what *really needs to be achieved*.
* Design the system so that when policies change (and they will), your software doesn’t break.

---

Would you like me to show a **diagram that visually separates requirement → policy → implementation**?
It’s one of the best ways to understand this concept permanently.



