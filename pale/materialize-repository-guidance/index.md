Title: Add coding instructions to a repository

[Read HTML](https://rawthoughts.in/pale/materialize-repository-guidance/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="add-coding-instructions-to-a-repository"></a>

# Add coding instructions to a repository

Pale supports two coding hosts today, Claude Code and Codex. Give either a shared way to review changes and check its work. Pale adds links to that guidance in the repository’s `AGENTS.md` and keeps the project instructions you already wrote there, including your build commands and conventions. Both hosts use this one entry file, with separate skills and references for each.

This setup installs guidance for your coding host. It does not start Pale’s resident service; your host reads and uses the installed instructions in its own session.

<a id="start-with-a-guidance-workspace"></a>

## Set up a starter workspace

Use a Git repository you can write to and a [local build of Pale](https://docs.rawthoughts.in/pale/getting-started#build-the-command-line-tool). In the same terminal, replace the three example paths below. Use a new folder name for `GUIDANCE_WORKSPACE` so the starter copies into that folder directly.

```sh
export PALE_SOURCE='/absolute/path/to/pale'
export PALE="$PALE_SOURCE/target/debug/pale"
export GUIDANCE_WORKSPACE='/absolute/path/to/new-guidance-workspace'
export REPOSITORY="$(cd '/absolute/path/to/your/repository' && pwd -P)"
cp -R "$PALE_SOURCE/docs/examples/guidance-workspace" "$GUIDANCE_WORKSPACE"
```

If you built the executable elsewhere, set `PALE` to its actual path. In `$GUIDANCE_WORKSPACE/machines/local.toml`, set `distribution_root` to your Pale checkout and `checkout_root` to the path from `printf '%s\n' "$REPOSITORY"`. Leave the other settings as they are.

Use this helper for the remaining commands. It keeps them pointed at the same starter and repository settings.

```sh
pale_here() {
  "$PALE" --workspace "$GUIDANCE_WORKSPACE/pale-workspace.toml" \
    --project repository --execution-workspace local-guidance --machine local "$@"
}

pale_here distribution-info --lockfile > "$GUIDANCE_WORKSPACE/distribution.lock.toml"
```

Keep `distribution.lock.toml` with the starter. If you update the Pale checkout, regenerate the lock and review a new plan before applying it.

<a id="choose-your-coding-host"></a>

## Choose your coding host

Set `PALE_HOST` for the host you want to use. The remaining commands use that choice throughout planning, installation, checking and removal.

| Host | Run this assignment | Generated guidance and skills |
| --- | --- | --- |
| Codex | `PALE_HOST=codex` | `.pale/guidance/codex/index.md` and `.codex/skills/` |
| Claude Code | `PALE_HOST=claude-code` | `.pale/guidance/claude-code/index.md` and `.claude/skills/` |

Choose one row and run its assignment in the same terminal. Read `AGENTS.md` before planning if it exists. If your repository points to shared rules elsewhere, keep that link and the rules it supplies. Existing client or upstream instructions keep their own conventions.

For Claude Code, use version 2.1.285 or later with its built-in `AGENTS.md` support enabled. Open `/config` and set **Project instructions** to `claude-md-and-agents-md` so Claude Code loads the shared file even when there are also `CLAUDE.md` instructions in the project or its parent directories. This is a host setting; putting it in the repository’s project or local settings will not enable it. See [Claude’s instruction-file settings](https://code.claude.com/docs/en/memory#choose-which-instruction-files-load) for user, managed or invocation configuration. Pale leaves your host settings and existing `CLAUDE.md` alone.

If an earlier Pale installation added its guidance to `CLAUDE.md`, first follow **Remove generated guidance** below with `PALE_HOST=claude-code` and that installation’s original workspace, project and repository selections. A newly copied starter cannot take over another installation. Review that removal, apply it, then return here for a fresh installation plan. Your own text stays in `CLAUDE.md`; the new contribution goes into `AGENTS.md`. Resolve any interrupted write before either operation, using the recovery link below.

<a id="save-the-plan-before-changing-repositories"></a>

## Review the changes

```sh
pale_here guidance plan --repository source --host "$PALE_HOST"
```

The plan lists files to `add`, `update`, `keep` or `remove`, followed by their text differences. Lines starting with `+` are additions; lines starting with `-` are removals. The surrounding text helps you see where each change belongs.

1. Find the proposed change to `AGENTS.md`. Check that your own instructions and any other host’s contribution are still there. Match each new link to a file in the plan.
2. Read the role and policies. The starter covers how to investigate a change, respect project rules and safety, and verify and review the work. Pale includes the instructions those policies depend on. For other roles or policies, see [choose Package guidance](https://docs.rawthoughts.in/pale/package-authoring#select-a-resource-for-the-actual-task).
3. Review the `.gitignore` change. Pale adds a block for its local lock, recovery record and remembered plans, preserving your existing rules. This works in ordinary repositories and linked worktrees.
4. Check every proposed path, especially removals. If Pale reports a conflict with an existing file, open it and agree on the change with the repository maintainer. Keep the existing instructions while you resolve it.

The plan leaves your instructions unchanged and remembers the proposal for this host. Each new plan replaces the previous one for that host. You can review the output in your terminal or save it by adding `> "$GUIDANCE_WORKSPACE/guidance-plan.txt"` to the command and opening that file. Keep saved output with the project: it can contain your project’s instructions.

<a id="apply-the-exact-saved-selection"></a>

## Apply the plan

When the changes look right, apply the plan with the same host and workspace settings:

```sh
pale_here guidance apply --repository source --host "$PALE_HOST"
```

Pale checks the files and settings again before it writes. If the plan has changed, generate and review a fresh one. When the command succeeds, it reports `Published source guidance` and the number of changed files.

Open `AGENTS.md` and follow the new role and index links. Check the guidance and skills at the paths in the host table. Start a fresh session of that host in this repository. In Claude Code, use `/memory` to confirm that `AGENTS.md` appears among the loaded files.

Then ask the agent running in that host to use the instructions for a small task, such as checking the links in a README. Follow its findings back to the actual links and destinations. Check which instructions it used and whether the result helps you fix the page. Seeing a file in the loaded list confirms that it reached the host; the task shows how the agent used it.

<a id="check-for-drift"></a>

## Check for drift

Run the planning command again. If the files and settings still match, every file is marked `keep`. Applying that fresh plan reports `0 changed files`. The plan from before installation is now out of date, so run a new one even when you expect no changes.

Review any proposed update before applying it. Pale can refuse to overwrite a file someone edited by hand, including its block in `.gitignore`. Compare that file with the proposed version and resolve the difference before you retry.

**Warning**

**Keep the interrupted-write record.** If a write was interrupted, keep `.pale-source-guidance-recovery.json` and [review the recovery choices](https://docs.rawthoughts.in/pale/interfaces/cli#review-and-install-package-guidance-before-activation) before running another apply. The CLI can help you restore the earlier files or finish cleanup after a completed write.

<a id="remove-generated-guidance"></a>

## Remove generated guidance

Plan the removal, review its output, then apply it:

```sh
pale_here guidance plan --repository source --host "$PALE_HOST" --intent remove
pale_here guidance apply --repository source --host "$PALE_HOST" --intent remove
```

Pale removes the selected host’s generated files and its contribution to `AGENTS.md`. Your own project text and the other host’s contribution stay. For an earlier installation recorded in `CLAUDE.md`, removal uses that recorded location. The local lock, remembered plan and their `.gitignore` rules also stay, ready for the next installation.

<a id="add-the-other-host"></a>

## Add the other host

Change `PALE_HOST` to the other value in the table. If you are adding Claude Code, first set its **Project instructions** as described in **Choose your coding host**. Then start again at **Review the changes**: read that host’s proposed files, apply its plan and try a small task in that host. Pale remembers a separate plan for each host; removing one host’s guidance leaves the other’s in place. The [developer contract](https://docs.rawthoughts.in/pale/interfaces/cli#review-and-install-package-guidance-before-activation) covers automation and recovery.


Reading path: [Pale](https://rawthoughts.in/pale/) > [Add coding instructions to a repository](https://rawthoughts.in/pale/materialize-repository-guidance/)


Source code for [Pale](https://github.com/getHarshOnline/pale) is credited to [Harsh Joshi](https://getharsh.in/about/).
