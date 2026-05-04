---
name: Copilot Instructions
description: Instructions for GitHub Copilot in this repository.
applyTo: **/*
---

# GitHub Copilot Instructions

# Whenever you cannot do something, you MUST follow these steps:
1. Never guess or make up an answer
2. Respond with "Can't do {task} because of {reason}"
3. Explain the reason
4. Suggest the best alternative approach, including unactivated tools
   - Suggestion MUST include research and reasoning, not just a guess
   - Use of web search is mandatory to have up-to-date information
   - At least, provide a *clearly* stated hypothesis based on research done


# All output generated should adhere to the following guidelines:
- English language including files names and content
- Use the user's language only when talking directly to him

# Repository - specialized agents
- https://github.com/RoGKoT/agents.git
   
# Agent expertise
- @time-management
  ↳ Timestamps agent
    ↳ timestamp-generator
    ↳ ↳ timestamp-validator
- @ssot-management