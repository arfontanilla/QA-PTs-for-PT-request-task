Here is the complete list of commands available in the QA Workflow Orchestrator v2.2 prompt:

Phase 1: Task Initialization
/start

Initializes the workflow and requests all required context variables.

Required variables: TASK_TITLE, TARGET_AUDIENCE, PT_REQUEST_DOC, PT_XML_SET, SKILLS_LIST, QUESTION_SET_ORDER, ID_PT_MAPPING.

/run html

Executes the [PROMPT: HTML_FORMATTER] to format the PT_REQUEST_DOC into a readable HTML block.

Does not update the Master Feedback Log.

/run progression_map

Executes the [PROMPT: PROGRESSION_MAP] to generate a TSV table combining QUESTION_SET_ORDER and ID_PT_MAPPING.

Initializes the Master Feedback Log with PT entries.

Confirms with: "✅ Master Feedback Log has been initialized with [X] PTs."

Phase 2: Iterative QA & Automatic Collation
/run alignment

Executes the [PROMPT: PT_DOC_ALIGNMENT] to check if PTs match the original request.

Collates feedback into the log under AI_FEEDBACK.

/run comprehensive

Executes the [PROMPT: COMPREHENSIVE_REVIEW] for a holistic PT review.

Collates feedback into the log under AI_FEEDBACK.

/run skill_check

Executes the [PROMPT: SKILL_MEASUREMENT] to verify PT-skill alignment.

Collates feedback into the log under AI_FEEDBACK.

/run check [check_name]

Runs specialized checks from [PROMPT: SPECIALIZED_CHECKS].

Valid check_name options:

hint_structure

forbidden_words

randomization_logic

language_tone

localization

grade_level

math_accuracy

solution_paths

realistic_randomization

Collates feedback into the log under AI_FEEDBACK.

Phase 3: Manual Input, Review & Final Reporting
/add_my_feedback [PT_ID]

Adds manual feedback for a specific PT to MY_FEEDBACK.

Confirms with: "✅ Your feedback for PT# [PT_ID] has been added."

/add_general_feedback

Adds general feedback for the entire set to GENERAL_FEEDBACK.

Confirms with: "✅ General feedback has been added to the log."

/show_feedback_table

Displays the Master Feedback Log as a TSV table with columns:
PT#, QuestionID, Difficulty level, Notes, AI FEEDBACK, MY FEEDBACK.

/generate_report

Generates a final ClickUp-formatted report synthesizing all feedback.

Follows strict structure:

Greets "Hi @Darwin Fernandez"

Lists GENERAL_FEEDBACK items.

Synthesizes AI_FEEDBACK and MY_FEEDBACK per PT (if non-empty).

Closes with "Thank you Darwin".

/help

Lists all available commands and their functions (this output).

