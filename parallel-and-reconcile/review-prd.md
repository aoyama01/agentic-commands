# Review PRD

<!-- /review-prd $ARGUMENTS -->

## Purpose

You should ask questions and provide feedback after reviewing the PRDs provided (file path = $ARGUMENTS).

Your questions will elicit the user's thoughts and increase the completeness of the PRD, thereby the autonomy of the subsequent design and implementation phases.

If the PRD is not complete before moving on to the next phase, there will be many differences and inconsistencies in subsequent phases.

## Input Validaiton

**IMPORTANT: First check if Issue number is provided as argument**

if `$ARGUMENTS` is empty, undefined, or not a valid file path:

- Display errorL `❌ エラー　：PRDのファイルパスが必要です。引数を指定して下さい。😅`
- Display usage example: `例: /review-prd path/to/prd-file.md`
- **STOP execution immediately - do not proceed with any subsequent steps**

Only proceed with the following steps if a valid file path is provided.

## Execution Steps

1. Read the design files, implementation files, and other information related to the provided PRDs throughout the project to understand the background information.

2. Based on the information gathered in 1, think of questions to ask the user to clarify any ambiguities or uncertainties when trying to generate a design and implementation from the current PRD.

3. Check the checklist to assure that the provided PRD meets the requirements.

- []: Include a TODO list, covering what needs to be done in design and implementation.
- []: Include all file paths to information sources such as primary information and references to relevant design and implementation files
- []: Include the file paths to which the design and implementation files will be written.
