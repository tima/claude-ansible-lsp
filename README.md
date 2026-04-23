# ansible-lsp

Ansible language server plugin for Claude Code, providing code intelligence features like diagnostics, auto-completion, hover documentation, and go-to-definition for Ansible playbooks and roles.

Powered by [@ansible/ansible-language-server](https://www.npmjs.com/package/@ansible/ansible-language-server) (>= 26.4.4).

## Features

- Real-time validation via ansible-lint (falls back to `ansible --syntax-check`)
- Smart auto-completion for plays, blocks, tasks, and module options
- Hover documentation for Ansible keywords, modules, and module options
- Go-to-definition for module source code

## Supported Extensions

`.yml`, `.yaml`

## Installation

```bash
# Install the Ansible language server
npm install -g @ansible/ansible-language-server
```

### From the official marketplace (once published)

Search for "ansible-lsp" in the `/plugin` Discover tab, or:

```bash
claude plugin install ansible-lsp
```

### Requirements

- Node.js >= 18
- Ansible 2.9+
- ansible-lint (recommended, for full validation support)
- @ansible/ansible-language-server >= 26.4.4 (`npm install -g @ansible/ansible-language-server`)

## Known Limitations

- Some LSP clients (including Claude Code) do not support `client/registerCapability` requests. ALS >= 26.4.3 handles this gracefully, but as a result:
  - Changes to `ansible.cfg`, `.ansible-lint`, or role `meta/main.yml` files require a server restart to take effect
  - Dynamic configuration change notifications are not received

## Local Development / Testing

To test changes to the plugin locally without publishing to the marketplace:

1. Clone the repository:

```bash
git clone https://github.com/tima/claude-ansible-lsp.git
cd claude-ansible-lsp
```

2. Create a `marketplace.json` in the `.claude-plugin/` directory:

```json
{
  "name": "ansible-lsp-marketplace",
  "owner": { "name": "Your Name" },
  "metadata": {
    "description": "Local marketplace for Ansible LSP plugin",
    "version": "1.0.0"
  },
  "plugins": [
    {
      "name": "ansible-lsp",
      "description": "Ansible language server for enhanced playbook and role intelligence",
      "source": "./"
    }
  ]
}
```

3. Register the local marketplace and install:

```bash
claude plugin marketplace add /path/to/claude-ansible-lsp
claude plugin install ansible-lsp@ansible-lsp-marketplace
```

4. Restart Claude Code to activate the LSP server.

5. To uninstall and clean up:

```bash
claude plugin uninstall ansible-lsp@ansible-lsp-marketplace
claude plugin marketplace remove ansible-lsp-marketplace
```

> **Note:** `marketplace.json` is gitignored and only needed for local testing.

## More Information

- [@ansible/ansible-language-server on npm](https://www.npmjs.com/package/@ansible/ansible-language-server)
- [Ansible Language Server documentation](https://github.com/ansible/vscode-ansible/blob/main/docs/als/README.md)
- [Upstream fix: ansible/vscode-ansible#2753](https://github.com/ansible/vscode-ansible/pull/2753)
