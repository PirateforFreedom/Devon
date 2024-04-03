<badges>

<logo>

# Devon : Open Source SWE Agent


# Usage

To use simply install using pip

```bash
pip install devon_agent
```
Set the Anthropic API key as an environment variable

```bash
export ANTHROPIC_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

Then you can use the agent to modify your code

```bash
devon_agent --goal "print hello world when the application starts" --path agent/src/main.py
```

# Features
- Reliable Multi File editing
- use tools such as git

# Coming soon
- UI for interacting with the agent
- Aplication generation from requirements 
- Find bugs in existing code
- SWE tasks such as architecture design, code review, and more
- Custom model for large context window and code ability

# About
Devin is an open source SWE agent that aims to help software engineers with development and maintinace of software. 

# Mission
Coding agents are extremely powerful and we beleive that the core of this technology should be open source. 
We are excited to be a part of the open source community and we are looking forward to collaborating with other developers to build a better future for software engineering.

# Contributing

If you would like to contribute to the project, please fill out this form:

[Contribution Form](https://forms.gle/yK8y2wjy3YyKg9XA9)


# Community

Join our discord server and say hi!
[discord](https://discord.gg/entropy)


# Devon!

Current agent strategy:

[] Max out 1 shot repo level code correction for 3 tasks: fill-in-the-middle, bug spotting, and completion
   [] for editing, JSON output should be good enough to contain metadata
s
prompt: update the existing main function with a surrounding loop until the user says stops

example usage: 

```
$ poetry run python src/state_functions.py

Please enter your repository git url: https://github.com/entropy-research/agent.git
Please enter your file path: agent/src/main.py
Please enter your goal: print hello world when  the application starts
Container created with ID: bdf8ffc5d719cf847e38037143ded2aa63a4270d67ba863cbc9d9b48b803ae96
Repository https://github.com/entropy-research/agent.git cloned inside the container.
SyntaxError: invalid syntax (<unknown>, line 1)
Reasoning
Fixing code
Applying diffs
import openaiimport osimport dotenvfrom anthropic import Anthropicdotenv.load_dotenv()def fix_code(broken_code):    client = Anthropic(        # This is the default and can be omitted        api_key = os.environ.get("ANTHROPIC_API_KEY"),    )    message = client.messages.create(        max_tokens=1024,        system="It's your job to solve bugs for people, people will present you with code and you should do your best to help them, its ok if you dont know, just say that",        messages=[            {                "role": "user",                "content": "```python print('hi) ```",            }        ],        model="claude-3-opus-20240229",    )    os.system("ls .")if __name__ == "__main__":    fix_code("bad_code")if __name__ == "__main__":    print("Hello, World!")    fix_code("bad_code")
Evaluating code
The changes made to the code do not fully meet the requirements. While the line `print("Hello, World!")` has been added under the `if __name__ == "__main__":` block, which will print "Hello, World!" when the application starts, the code still contains the `fix_code` function and its associated logic.

To fully meet the requirement of printing "Hello, World!" when the application starts, you should remove the unnecessary code and keep only the relevant parts. Here's the modified code that meets the requirement:

<NEW_CODE>
import os
import dotenv

dotenv.load_dotenv()

if __name__ == "__main__":
    print("Hello, World!")
</NEW_CODE>

In this modified version:
- The unnecessary imports (`openai` and `anthropic`) have been removed since they are not used.
- The `fix_code` function and its associated logic have been removed as they are not relevant to the requirement of printing "Hello, World!" when the application starts.
- The `print("Hello, World!")` statement remains under the `if __name__ == "__main__":` block, ensuring that it is executed when the application starts.

With these changes, the code now focuses solely on printing "Hello, World!" when the application starts, meeting the stated requirement.
Container destroyed.
```
