# SharpClaw.Modules.VSCodeEditor

`SharpClaw.Modules.VSCodeEditor` adds SharpClaw tools for a connected VS Code
workspace. The module defines file, selection, diagnostics, diff, build, and
terminal actions, then forwards each action through the shared editor bridge
instead of reading or writing workspace files directly from the SharpClaw host.

Install this package with `SharpClaw.Modules.EditorCommon`. At runtime the
module requires the common module's `editor_bridge` and `editor_session`
protocol contracts so it can resolve the selected editor session and deliver
the request to the VS Code extension that owns the workspace.

The module checks that a connected session is a VS Code session before it sends
an action. If the selected session belongs to a different editor, execution
stops with a clear error so the caller can use the matching editor module.
