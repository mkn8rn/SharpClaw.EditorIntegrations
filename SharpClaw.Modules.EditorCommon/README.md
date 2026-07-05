# SharpClaw.Modules.EditorCommon

`SharpClaw.Modules.EditorCommon` provides the shared runtime surface used by
SharpClaw editor integrations. It registers the editor WebSocket endpoint,
tracks connected IDE sessions, stores editor session records through the
SharpClaw module storage gateway, and exports protocol contracts that
editor-specific modules can call.

Install this package when a SharpClaw application runtime should accept editor
connections from IDE extensions. The package should be loaded with editor
module packages that depend on its `editor_bridge` and `editor_session`
contracts, such as the VS Code and Visual Studio 2026 editor modules.

The module does not expose LLM-callable editing tools by itself. It supplies the
connection and session infrastructure that lets editor-specific modules forward
read, write, selection, diagnostics, diff, build, and terminal requests to the
correct connected workspace.
