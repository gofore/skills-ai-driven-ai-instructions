## Step 2: Supporting Multiple LLMs

You've created a great "source of truth" `AGENTS.md` file. But what happens when you use different AI tools, each with its own instruction file format? In this step, you'll learn how to support multiple LLMs without duplicating your instructions.

### 📖 Theory: A Single Source of Truth

Different developers on your team might use different AI assistants. Some might use GitHub Copilot, others might use Claude, and some might use Cursor. Each of these tools looks for a different instruction file.

Instead of copying and pasting your instructions into each file (which would be a maintenance nightmare), you can use your `AGENTS.md` file as a single source of truth and simply reference it from the other files.

This has several advantages:
*   **Maintainability:** When you need to update your instructions, you only need to edit one file.
*   **Consistency:** All AI assistants will be working from the same set of instructions.
*   **Flexibility:** Developers can use their preferred AI tool without sacrificing consistency.

### ⌨️ Activity: Create Your LLM-Specific Instruction Files

Your task is to create instruction files for GitHub Copilot and Claude, and have them reference your `AGENTS.md` file.

1.  Create a new file named `CLAUDE.md` in the root of this repository.
2.  Create a new file named `copilot-instructions.md` in the `.github` directory.
3.  Use your favorite AI assistant to generate the content for these files. Use the following prompt:

    > "Generate the content for `CLAUDE.md` and `.github/copilot-instructions.md`. These files should be very brief and simply reference the `AGENTS.md` file as the primary source of truth for project guidelines. Add a note that tool-specific instructions can be added to these files if needed."

4.  Commit and push the new files to your repository.

Once you've pushed the files, a GitHub Actions workflow will automatically check your work.
