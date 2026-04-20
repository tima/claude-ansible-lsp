# Example Playbooks

This directory contains example Ansible playbooks for testing the LSP functionality.

## Files

- **playbook.yaml** - Simple working playbook to verify basic functionality
- **webapp-deploy.yaml** - Realistic deployment example
- **broken-playbook.yaml** - Contains various Ansible-specific errors (undefined variables, typos, invalid handlers)
- **syntax-errors-playbook.yaml** - Contains YAML syntax errors for testing parser diagnostics

## Testing the LSP

Open any of these files in Claude Code to see the language server in action:

1. **Working examples** (`playbook.yaml`, `webapp-deploy.yaml`) - should show auto-completion and hover docs
2. **Error examples** (`broken-playbook.yaml`, `syntax-errors-playbook.yaml`) - should show diagnostics and error highlighting
