# FTE Bronze Project

A task management and file-watching system that automates the processing of incoming tasks.

## Overview

This project implements a workflow for handling tasks through various stages:
1.  **Inbox:** Incoming files are placed here.
2.  **Needs_Action:** The `file_watcher.py` script automatically processes files from the `Inbox` and creates a Markdown task in the `Needs_Action` folder.
3.  **Done:** Once tasks are processed according to the `Company Handbook`, they are archived in the `Done` folder.

## Project Structure

- `Inbox/`: Landing zone for new files to be processed.
- `Needs_Action/`: Markdown files representing tasks that require attention.
- `Done/`: Archived tasks and original files (in `Done/Originals/`).
- `file_watcher.py`: Python script that monitors the `Inbox` and moves files to `Needs_Action`.
- `Company_Handbook.md`: Documentation defining the "Process Task" skill and its sequence.
- `Dashboard.md`: High-level overview of pending and completed tasks.
- `System_Logs.md`: Historical log of actions performed by the system.
- `Plans/`: Directory for development plans or strategies.
- `Logs/`: Directory for detailed logs.

## Getting Started

### Prerequisites

- Python 3.x

### Running the File Watcher

To start monitoring the `Inbox` directory for new files:

```bash
python file_watcher.py
```

### Workflow

1.  **Add Tasks:** Drop any file into the `Inbox/` directory.
2.  **Automatic Conversion:** The script will create a Markdown version of the file in `Needs_Action/`.
3.  **Process Tasks:** Follow the instructions in `Company_Handbook.md` to process the tasks in `Needs_Action/`.
4.  **Archive:** Completed tasks are moved to the `Done/` directory.

## Task Processing Sequence

The `Company_Handbook.md` defines specific prompts and triggers for task execution:

### Trigger: 'Process Task'

When the **Process Task** trigger is activated, follow this sequence:

1.  **Read Files:** Read all Markdown files inside the `Needs_Action` folder.
2.  **Analyze Context:** Understand the context of each file and mark its internal status as 'Completed'.
3.  **Archive Task:** Move the processed Markdown file into the `Done` folder.
4.  **Update Dashboard:** Update `Dashboard.md` by moving the task name from the 'Pending Tasks' section to the 'Completed Tasks' section.
5.  **Log Activity:** Append a short entry to `System_Logs.md` detailing the processed tasks and actions taken.

### File Watcher Output

When a new file is detected in `Inbox`, the script writes a Markdown file with the following prompt structure:

```markdown
# Task: [Filename].md
Source: [Original Filename]
Status: Pending

## Content
[File Content]
```


### Prompts

Gemini said
Here is an analysis of the Bronze Tier requirements and a set of prompts designed to initialize and build your foundational AI Employee.

When architecting this foundation-layer autonomous agent, establishing a clean local-first file system and robust Python sentinel scripts early on is critical for later scalability into more complex multi-agent setups.

Bronze Tier Analysis: The Minimum Viable Agent
The Bronze Tier focuses strictly on establishing the core Perception → Reasoning → Action loop in a localized environment without external API complexities (like Odoo or social media).

GUI / Memory: Obsidian vault with a strict folder taxonomy (/Inbox, /Needs_Action, /Done).

Rules Engine: Dashboard.md (state) and Company_Handbook.md (constraints).

Perception: A single Python Watcher script (File System or Gmail) functioning as the trigger.

Reasoning/Action: Claude Code executing file operations using native Agent Skills.

Phase 1: The Initialization Prompt (For Claude Code)
Feed this prompt directly into Claude Code in your terminal to have it build the Bronze Tier infrastructure for you.

System Context: You are an expert AI engineer assisting a technical project lead in building a local-first, autonomous "Digital FTE" (Full-Time Equivalent) agent. We are currently implementing the "Bronze Tier" foundation layer.

Task: Initialize the core architecture for my Personal AI Employee. Please execute the following steps sequentially using your file system skills:

Initialize the Knowledge Base: Create an Obsidian vault structure in my current directory named AI_Employee_Vault. Inside it, create three folders: Inbox, Needs_Action, and Done.

Establish the Rules Engine: Create a Company_Handbook.md at the root of the vault outlining basic operational rules (e.g., "Read /Needs_Action first," "Never delete files, only move to /Done," "Log all actions").

Establish the State Dashboard: Create a Dashboard.md with a clean markdown layout tracking pending items, completed items for the day, and system status.

Build the Watcher (Perception Layer): Write a robust Python script named filesystem_watcher.py using the watchdog library. This script should monitor the Inbox folder. When a new file is dropped in Inbox, it should automatically move it to Needs_Action and append metadata (timestamp, original filename) to the top of the file in markdown format.

Define Agent Skills: Generate a skills.json or markdown documentation detailing the specific Agent Skills you will use to read the Needs_Action queue, process the text, update the Dashboard.md, and move the processed file to Done.

Please confirm once the folder structure, markdown files, and Python watcher script have been generated locally.

Phase 2: The Agent's Persona Prompt (For the Company_Handbook.md)
Once the system is built, this prompt acts as the persistent system instruction for the AI Employee when it wakes up to process tasks.

Role & Identity:
You are a Bronze-Tier Digital FTE. You operate entirely within a local markdown-based environment (Obsidian). Your primary function is to process raw inputs, structure them, and maintain an updated operational dashboard.

Standard Operating Procedure (SOP):

Assess: Whenever you are triggered, immediately check the /Needs_Action directory for new markdown files.

Process: Read the contents of the pending files. If the file contains raw notes, format them into clean, actionable bullet points. If it contains data, summarize it.

Update: Open Dashboard.md. Append a summary of the processed task under the "Completed Today" section. Update the "Pending Items" count.

Close: Move the processed file from /Needs_Action to /Done. Never permanently delete user data.

Iterate: Use the Ralph Wiggum stop-hook pattern to verify that the /Needs_Action folder is completely empty before you terminate your run.

Constraints:

Always act autonomously to complete the pipeline; do not wait for human intervention unless a file explicitly requests approval.

Maintain strict adherence to local file system operations—do not attempt to call external web APIs unless explicitly authorized by an MCP server integration.
