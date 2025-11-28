# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a Git learning and reference repository containing documentation and guides for:
- Setting up Git configuration
- Establishing SSH authentication with GitHub
- Creating and pushing repositories to GitHub
- Common Git workflows and branch operations

## Content Structure

The repository contains primarily educational documentation:

- **README.md** - Comprehensive guide covering:
  - Git global configuration (username, email, branch defaults, editors)
  - SSH key generation and setup (Ed25519 and RSA options)
  - Platform-specific commands for Windows, Linux, and macOS
  - Two workflows for repository creation/pushing
  - Branch merging and conflict resolution

- **git.txt** - Quick reference example showing real-world Git workflow with actual output

## Key Topics Covered

### Git Configuration
- Global vs. local configuration settings
- Setting username and email
- Default branch naming conventions
- Credential and editor configuration

### SSH Authentication
- Why SSH keys are preferred over HTTPS
- Ed25519 and RSA key generation
- SSH agent configuration (platform-specific)
- Adding keys to GitHub
- Connection testing

### Repository Workflows
- Initializing new local repositories
- Pushing existing repositories
- Branch operations and renaming
- Merging branches and resolving conflicts
- Push/pull operations

## Important Notes

- The repository uses SSH authentication (`git@github.com:` URLs) as the recommended approach
- Documentation includes platform-specific commands for Windows PowerShell, Linux, and macOS
- The guide emphasizes setting up SSH keys before making commits
- Two main approaches are documented: creating new repos locally vs. pushing existing repos

## Common Development Tasks

### Adding/Updating Documentation
When making changes to README.md or git.txt:
- Ensure examples are accurate and tested
- Include platform-specific variations when relevant
- Maintain clear command explanations
- Keep the documentation organized in logical sections

### Verifying Examples
Test commands in appropriate environments before updating documentation, particularly for:
- SSH key generation and setup
- Cross-platform command variations
- GitHub authentication workflows
