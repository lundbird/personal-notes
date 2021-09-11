# How to be a Senior Engineer
#growth #engineering
Generally just being as detail oriented as possible. Git blame and git history, and commit and ticket history can help with this. Don’t forget small details at the end of a task. LIke deploying changes

Formulizing assumptions and predicting future use cases is the skill that makes a senior software engineer. Performing these tasks at the beginning will prevent you from spending significant amounts of time implementing a solution, only to find that it is unfeasible or not ideal.

 When performing a task one should consider and brainstorm the following:

Assumptions
- verify these if possible
- ask “Could this cause an issue and how?”
Future use cases
Maintainability
Safety
- How can we make the change safer.
Testing plan
- Perform positive and negative tests and do the negative case first.
- Corner cases
Failure cases
   For each failure case:
   - mitigation
   - rollback 
   - monitoring
Dependencies
- Can this change break anything?
- What other projects need to be updated?
- Who needs to be made aware of changes?
- Can we do a partial rollout?
Integrations
- logging
- developer tools (eg data grip for iam auth)
- CI (eg new jobs for test environment)
- infrastructure
Monitoring
Security
- PII
- RBAC
- auditing
- other access controls like firewalls
Cleanup Tasks
- Clean up any test or development resources
- Revoke any temporary authorization or test users
- Ensure the active config matches what is on the master git branch.
- Think of more automation. Why not do everything through cli and code? Often your first solution doesn’t automate enough and could do more. Give it some time for deep thought.


Soft skills
- Err on the side of over communication rather than undercommuniqation
- When performing a change, think of the affected parties and give them a heads up. Communicate as soon as possible
- In meetings, request a follow up instead of giving more detail
- Look ahead to upcoming meetings and have an idea of what you want to get accomplished. 
- Follow up with more people on their issues to ask if they need assistance or clarification and to give updates. Small things like this go a long way


OTHER
- DONT MAKE NEW CHANGES AFTER 6PM. 
- Every person will think of problems and work a little differently than you do. Try to spot these differences and see how you can improve your own workflows. You should be able to learn something from just about everyone if you put in the effort.


TESTING:
- One issue I face is not testing thoroughly and verifying the state of the system before apply, then checking after to ensure that it was applied successfully and works as expected.
- Just check the logs? This catches 90% of issues lol. If it doesn’t then you should fix the logging.
- Just run a quick regression suite. Its free and takes under 10 minutes.
- Prototyping should be specific (does this work? Does this support 90/10 between these two services?)
- Find a way to script the testing. Very common that I push a MR and something tiny breaks even on the smallest change. Adhoc manual testing is not great because you can forget to do it on every change

Design:
- Code complete cheatsheet

Planning:
Make a plan. Then come back to it a week later to give yourself a review.
Go take a literal walk then try to brute force

Other:
- Remember global search is your best friend to search for dependencies and understand blast radius

Keep asking questions when you do things and ask if what you are doing is safe. 

Remember that its okay to mess up, as long as you make improvements and learn from it.


- Commit to git and don’t take shortcuts for manual changes.
- Read the official docs

Follow a task all the way to completion from dev to prod.

Think of the big picture. The template generation for service profile is a good example. Why not do this? Make it an improvement all the way.
