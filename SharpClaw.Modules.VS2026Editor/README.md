# SharpClaw.Modules.VS2026Editor

`SharpClaw.Modules.VS2026Editor` adds SharpClaw tools for a connected Visual
Studio 2026 workspace. The module defines file, selection, diagnostics, diff,
build, and terminal actions, then forwards each action through the shared editor
bridge instead of reaching into the workspace from the SharpClaw host process.

Install this package with `SharpClaw.Modules.EditorCommon`. At runtime the
module requires the common module's `editor_bridge` and `editor_session`
protocol contracts so it can resolve the selected editor session and deliver
the request to the Visual Studio extension that owns the workspace.

The module checks that a connected session is a Visual Studio 2026 session
before it sends an action. If the selected session belongs to a different
editor, execution stops with a clear error so the caller can use the matching
editor module.
