# Debugging

## Diagnostic Principles

1. Do not guess by reading code
2. Reproduce the actual issue using e2e tests / API tests

## Debug Workflow

Use the `todo` tool to create the following items:

Problem Verification -> Environment Setup -> Issue Reproduction -> Issue Fix

## Problem Verification

If context is incomplete or the user only provided partial information, proactively communicate with the user to gather missing context. Use the `ask` or `question` tool.

When the user explicitly states there is nothing more to add, proceed to the next step.

## Environment Setup

Use the `@general` subagent to set up the environment: use [[git.md]] for branch management. For each investigation, create a new `worktree` based on the current branch, with `<type>` set to `issues` and `<slug>` being a short name for the verified issue. Perform all subsequent operations in this new `worktree`.

In this `worktree`, use [[dev/ref/aspire-skill.md]] `aspire` to start the relevant services. Once ready, proceed to the next step.

## Issue Reproduction

Based on the information gathered from the user, attempt to reproduce the issue using e2e or API tests. This may include screenshots, browser state inspection, and other investigative手段.

## Issue Fix

Use the `@general` subagent to fix the issue: fixes are made in the `worktree`. Once fixed, submit a `pull request` for user review.

When fixing, write e2e tests or API tests to prevent similar issues from recurring.