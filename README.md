# SharpClaw Editor Integrations

SharpClaw editor integration packages add IDE-aware tools to a SharpClaw
runtime without making the runtime depend on a local source checkout of the
default editor modules. Use `SharpClaw.Modules.EditorCommon` when the host needs
the shared editor bridge, session storage contract, REST session endpoints, and
WebSocket connection point used by concrete editor modules.

Use `SharpClaw.Modules.VSCodeEditor` when a SharpClaw runtime should expose
tools that talk to a connected VS Code workspace through the editor bridge. The
module defines read, write, selection, diagnostics, diff, build, and terminal
actions, then delegates execution to the connected editor session instead of
directly touching workspace files from the SharpClaw process.

Use `SharpClaw.Modules.VS2026Editor` when the same tool surface should target a
Visual Studio 2026 extension session. It validates that the selected editor
session is connected to Visual Studio 2026 before forwarding actions through the
shared bridge, which keeps the VS Code and Visual Studio tool paths distinct at
runtime.

The module packages are intended for SharpClaw application runtimes that already
load SharpClaw .NET modules from package payloads. A host should install the
common bridge module together with whichever editor-specific modules it wants to
offer, then scan the packaged `sharpclaw` payload so the module manifest and DLL
are available next to the host assembly at runtime.
