## Rivet – Visual Programming for LLM Agents

**Rivet** is an open-source visual programming environment for building AI agents that use large language models (LLMs). It enables teams to design, iterate, test, and deploy prompt-based logic using a visual interface known as a **prompt graph**.

### Key Features

* **Prompt Graphs**: You create logic flows visually, where each node represents a specific action, like sending a prompt to an LLM, performing a conditional check, or calling an external API.
* **Iterative Development**: You can rapidly modify and test prompts without needing to write and re-run code from scratch.
* **Debugging Support**: Rivet provides tools to inspect intermediate steps and outputs, making it easier to understand how your agent is behaving.
* **Team Collaboration**: Multiple users can contribute to the same project, improving coordination between engineers, designers, and product managers.
* **Deployment Flexibility**: Once your agent is ready, you can run it directly in your own application or export it as code.

### How It Works

1. **Build Prompt Graphs**: You visually drag and connect components in a flowchart-like interface. Nodes can represent user inputs, LLM calls, conditionals, data transformations, and more.
2. **Chain LLM Calls**: Multiple LLM prompts can be connected in sequence, with the output of one becoming the input of the next.
3. **Inspect Outputs**: At each node, you can inspect the actual response or data flow, helping you identify and fix logic or prompt issues.
4. **Export or Deploy**: The final logic can be exported as reusable code or deployed within your application.

### Advantages of Using Rivet

* Easier to debug and iterate on prompts compared to writing code directly
* Enables non-technical users to participate in LLM development
* Reusable prompt components help manage complexity
* Self-hostable and open-source, giving full control over deployment and customization

### Typical Use Cases

* A chatbot that guides users through complex processes, like applying for a loan or submitting a tech support ticket
* A multi-turn AI tutor that adapts questions based on a student’s prior answers
* An intelligent assistant that integrates with APIs and uses LLMs to generate summaries, reports, or insights

### Who Uses Rivet

* AI developers and engineers building multi-step agents
* Designers prototyping conversational flows
* Organizations developing internal LLM tools or customer-facing AI features
