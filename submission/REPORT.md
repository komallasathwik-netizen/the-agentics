# CrewAI Build Report

**Name:** Sathwik Komalla
The topic I selected was Healthcare Price Transparency.

## 1. What I changed

I changed the voice of the crew by editing the `Writer agent's backstory` in `crewai/main.py`. As the original backstory was for a general technical writer, this explainer was a fairly technical summary of the story. I made it up into a story about a patient advocate who has no medical or insurance experience, but is writing for the general public. The new backstory directs the agent to refrain from using jargon, to explain key terms in common terms, to utilize common analogies (such as describing the price at a grocery store), and to conclude with action steps that the patient can take. I have also changed the `expected_output` of the Writer's task, making it request a friendly explanation of around 400 words, including 1 analogy and a short list of "What you can do" at the end.

The change was made because the subject of healthcare price transparency is one that is most important to the patient yet is typically communicated in policy and legal jargon. It also integrates with my capstone project, CareNavigator, a resource for researching health care costs. Testing whether or not the agent's backstory actually affects the output is an obvious and obvious method, which is to change the audience.

## 2. How CrewAI works

CrewAI creates a workflow out of 3 main parts. An agent is an LLM that has been provided with a role, a goal and a backstory. These fields are converted into the agent's instructions, therefore influencing the way it thinks and writes. A task is a specific task to do with it having a `description`, an `expected_output` and an assigned agent. The `expected_output` serves as a guide to the agent of the final output. Groups of agents and tasks that are run together are called a **crew**. The tasks in this kit is executed in the following order: **sequential**: The output of one task is processed to the input of another task. The research-style task generates the content, which then is turned into the final explainer by the Writer and saved to `output/explainer.md`.

My change was successful because the background of the Writer and its task's `expected_output` is the part of the prompt that the model receives in running on that task. I didn't change anything, so the same type of data was collected for the earlier task regarding price transparency. However, when the Writer got the news, the instructions in it changed and instructed it to write for an "ambiguous patient", a general reader. That altered the tone, vocabulary and grammar of the concluding explainer, without changing the underlying subject matter. It also demonstrates that in CrewAI, most behaviour is configured in natural language and not in code logic.

## 3. Evidence

<!-- TODO: Add this from YOUR two files. Use actual observations and short examples to replace the brackets.

The two outputs are: `explainer_run1.md` (original kit) and `explainer_run2.md` (changed Writer).

- Tone and vocabulary: in run 1, the explainer [described without defining these terms: machine-readable files, negotiated rates]. It [describe, e.g. explained these in simple terms, such as...] in run 2.
Structure: Run 1 [Describe layout]. Run 2 [describe, e.g. ended with a "What you can do" list with steps such as ...].
Length and focus: Run 1 was around [X] words and was focused on [policy / hospitals / regulations]. Run 2 was for [Y] words and targeted [what patients can actually do].

One real thing that surprised me, or went wrong, e.g. the run was longer than anticipated, formatting issues became apparent after editing the backstory, writer exceeded word limits, or jargon remained in the output. Then mention what you did, such as added a comma, added “expected output” or re-ran it.

## 4. Choosing a framework

I would select CrewAI to work on a project where the tasks break down into distinct tasks, such as one task being done by the researcher, collecting data on costs, and the other by the writer, where they explain it to the patient. This is easily expressed with CrewAI, since each role is simply an agent for a role, goal and backstory, and they are simply executed in sequence by the crew. As I demonstrated in this assignment, I can alter the behavior of the entire system by editing a few lines of configuration text, while keeping all my control-flow code intact.

If I were to write the graph out, with nodes, edges and state, in LangGraph, this simple pipeline would have been more cumbersome. But it would be simpler with LangGraph to loop back to the researcher if missing info is discovered by the writer, to add conditional branches (such as different for insured vs uninsured patients), etc., and to keep a tight record of what state is maintained between steps. If a production version of CareNavigator is being designed where every step has to be reliable and the ability to step back and see what is happening to an object is important, then LangGraph's explicit structure might be preferable. CrewAI is faster and simpler for a rapid prototype with clear roles.

## 5. Use of AI and verification.Use of verification and AI.

Verification: The kit does not have web access, so all of the facts in the output are from the model's memory and could be incorrect or stale. I have verified the primary statements in both explainers with official sources, primarily CMS (cms.gov). Additionally, I evaluated whether the output correctly represented the intended audience by determining if the output was understandable to an individual who was not familiar with the terms.

AI use: I used Claude (an AI assistant) to provide step-by-step guidance for this assignment, draft the three back story ideas I selected, and to draft and organize this report. I edited the report to show evidence from my own output files and adapted it as much as possible to my own interpretation and running. It was confirmed that the code was changed by running the kit to see that it completed and the output changed as expected.