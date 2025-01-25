### What do I think about you and your experience.
You hopefully know by know, that I like your attitude and that I admire the effort you put in your thoughts and writing. And I like the outcome of that and that it does make sense.

But, also quite frankly, it seems to me that you are young and will have more experiences throughout your life. You will grow &mdash; as I have done, but hopefully with another end result (otherwise, how would humanity grow, if we only were to repeat ourselves).

Given your perspective and assumed experience, what you write is a logical conclusion and does make total sense. On the other hand you are not a first with your line of thought about "Flows". Functional decomposition was given as an example of my Professor of a bad architecture, because &mdash; you guess it &mdash; of its repetition in the 1990ies. The patterns you will find are simple, if that is your *only* guideline. So, what it tells you about the structure of your code is little.

### Hard to understand code. Why must it be so complicated?

I assume, you have made the experience, that code can be hard to understand. When trying to understand the code someone else wrote, you have to dive down into their levels of abstraction, looking for and understanding data and data structures which are not natural to the problem at hand.

Can't we just write code, which follows the natural flow of things? Which describe the feature/problem at hand in the problem domain? These are natural question and you found the write answers. 

The unsolved problem is *when* to follow The-River and when to use abstraction and, if so, to which level? 

### Your personal experience

I guess and assume a lot about you as a person and about your experience. I should be all wrong, because I know rather nothing about you:

* Did you work on large projects without being in control? Control means: Being a moderator or the main contributor.
* Have you worked in a team &mdash; as opposed to "with others"?

Through such experiences you might learn that *your* understand of "natural" if different from what others consider "natural". Neither of you is right or wrong. 

### My personal experience

I did bad decomposition / abstraction in the past and experienced it from others, see below. I can support your assumptions on wrong abstraction. That is, why I believe, it makes sense for others to read your thoughts and learn from them.

#### Strict rule in my teens

To avoid repeating I came up with the following rule: "If three statements are the same in two different functions, then create a new function and call it instead."

This of course is rubbish and way to strict, but it is where the general do-not-repeat-yourself statement lead me. I do not know, if I actually stuck to the rule eventually; hopefully not.

#### Weird obedience to the "Short-Function" rule.

A member of my team was not a very good programmer. I had to review his code and provide him with feedback. Our code-checker at the time reported lengthy functions. As it was stupid it just counted lines and told you: "That function is 250 lines > 70 lines".

His member functions were way longer and did touch different levels of hierarchy/abstraction. I assume, they would have broken your River-Guidelines as well. But, he did not move the stuff on the "lower" levels into private function to be called by the original function. That way, the original function would still show the whole flow, but on a "higher" level. 

Instead he just cut the function in half. So the first half remained in the original function and the second half would move into a new function. Unfortunately the context of the first half needed to be passed ot the second half, so he moved all of that into member fields. Therefore, the class abstraction also became completely obscured. 

I am not telling this, to bash on that colleague, but to support your claim that existing rules can be misinterpreted, and bending them for good reason does make sense. I consider your thinking a good reason.

#### How we wanted to use flow in my domain of work

I am working in diagnostics of vehicle electronics. 60-80 micro controllers (ECUs) are installed in a single vehicle and most of them need to be configured, checked, updated and at some point in time probably replaced. If you support multiple vehicle models you have multiple such setups. A successor model will have carry-over ECUs which are similar, but not necessarily identical to the predecessor model.

Many of these things are very specific flows. Each flow is mostly independent of others. Specifications for such operations are provided as flow charts. I believe The-River fits perfectly.

The company developed a domain specific language which should allow the people who work for manufacturing or after sales (work shops) create those flows quickly. One group of authors (developers) is usually responsible for a specific vehicle model or subset of those ECUs. They do not want any change by other teams influence their work, so they somehow try to avoid reuse. The language is a graphical flow-chart language. 

The idea was to create new scripts quickly whenever you need a new sequence to handle some requirement. Quickly adapt if a change is required to a local script. Adding a little to a local sequence would just require a little change to the implementing script. Surprises should have been avoided, that adding little functionality would cause much higher efforts than the original change, because of implied refactoring.

I believe to this day, that supporting The-River is the right thing to do there.

We failed. But that is not an argument against The-River, but an example of not pursuing it hard enough. Unfortunately it is also an example, why we need other options as guidelines.

Why did we fail:
* The tool was not fast enough. Creating a script was not a thing of seconds.
* The base layer's were not powerful enough. In your example you call `parsed_item = parse_item(item)`. If you have no `parse_item` function, you create your own script. 
* We asked more from the tool than it was designed for. Instead of creating scripts for each ECU, we created general reusable script that implemented the same thing for multiple ECUs. This resulted in parameterization, concurrency and a complexity that the scripting language could not handle well.
