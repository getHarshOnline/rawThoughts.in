Title: Inspect your workspace

[Read HTML](https://rawthoughts.in/pale/inspect-your-workspace/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="inspect-your-workspace"></a>

# Inspect your workspace

You want a repository to use a security-review role, and need to know what else depends on that choice. Before installing the new guidance, check what Pale would use for the project on this computer and compare the proposed edit with the current workspace.

**Important**

**Use your existing workspace.** The [repository guidance starter](https://rawthoughts.in/pale/materialize-repository-guidance/) is enough to try the role comparison. The runtime checks also need a Package distribution and machine paths set up.

<a id="choose-the-configuration-you-mean"></a>

## Choose the configuration you mean

Use the terminal where you set `PALE` in the [source-build instructions](https://docs.rawthoughts.in/pale/getting-started#build-the-command-line-tool). Find the root `pale-workspace.toml`, the project's ID, the ID of the setting it runs in and the machine ID. Use the IDs in your workspace files. The machine binding supplies the paths and executables on this computer.

Point `CURRENT_WORKSPACE` at the workspace you use now. For the repository guidance starter, set the three IDs to `repository`, `local-guidance` and `local`, respectively. For a runtime workspace, replace the example IDs with its own project, execution workspace and machine IDs. Keep the same shell open so you can reuse `pale_here` below.

```sh
CURRENT_WORKSPACE='/absolute/current/pale-workspace.toml'
PALE_PROJECT='demo'
PALE_EXECUTION_WORKSPACE='default'
PALE_MACHINE='local'

pale_here() {
  "$PALE" --workspace "$CURRENT_WORKSPACE" --project "$PALE_PROJECT" \
    --execution-workspace "$PALE_EXECUTION_WORKSPACE" --machine "$PALE_MACHINE" "$@"
}
```

If you are using the repository guidance starter, continue to [compare the role change](https://rawthoughts.in/pale/inspect-your-workspace/#compare-a-candidate-without-applying-it). For a runtime workspace, check the current configuration first.

<a id="check-the-selected-world"></a>

## Check a runtime workspace

```sh
pale_here validate
```

If validation reports a missing declaration, machine path or Package file, fix that input and run it again. This check leaves repository files alone. Check whether an application is running through the application itself.

Then read the compiled profile:

```sh
pale_here summary
```

Check `project_id` and `execution_workspace_id`, then look at each entry in `repositories`:

| Field | What it tells you |
| --- | --- |
| `repository_id` | Which repository this entry describes |
| `surfaces` | The guidance and settings Pale would generate |
| `execution_paths` | The ways this repository is configured to run work |
| `activation_selected_execution_path_ids` | Which paths are configured for activation in this repository |

If a repository or agent path is missing, check how it is linked to the project and which Packages it uses. A listed path tells you how the workspace is set up. Use `pale_here compile` if you also need the generated file counts and checksums from the compilation.

<a id="compare-a-candidate-without-applying-it"></a>

## Compare a candidate without applying it

Keep the proposed workspace in a separate folder. Use the same project, execution workspace, machine and Package distribution. Keep the project's starting Package list the same. To change the distribution or that list, validate each copy against its own Package inputs and inspect the results separately.

If you set up the repository guidance starter, copy its whole folder, including the locks, to a new folder. Leave the copy pointed at the same repository and Pale checkout. In its `pale-workspace.toml`, change the repository role's `resource_id` from `change` to `security`. Keep `CURRENT_WORKSPACE` pointed at the original starter. Set `CANDIDATE_WORKSPACE` to the edited copy.

```sh
CANDIDATE_WORKSPACE='/absolute/candidate/pale-workspace.toml'

pale_review() {
  pale_here review-configuration --candidate-workspace "$CANDIDATE_WORKSPACE" "$@"
}

pale_review preview > review.json
```

In `review.json`, check `project_id` and `execution_workspace_id`. Look at `profile_change.state`. If you changed the starter's role, it should read `changed`. Then read the first page of up to ten entries:

```sh
pale_review impacts --limit 10 < review.json
```

If `nextOffset` is a number, run the command again with `--offset NUMBER`, using that number and the original `review.json`. A `null` value means you have reached the end.

A `state` of `affected` means the item depends on something you changed. Its own value can still be the same. In the starter example, inspect the affected entries, including `workspace-manifest` and `responsibility_closure`, to see which parts of the workspace depend on the role. For a runtime workspace, run `summary` for both copies with the same IDs to compare their resulting settings. To inspect individual values from an integration, see [how configuration review works](https://docs.rawthoughts.in/pale/workspace#review-a-proposed-change).

Each request checks the saved preview against a fresh comparison. If you edited either workspace since the preview, run `pale_review preview` again and review the new results. Leave the old JSON alone.

**Important**

**Accepting a review does not apply it.** To accept the review, run `pale_review accept < review.json`. Use `reject` or `cancel` for those decisions. Pale returns your decision and leaves both workspaces and repository files as they were.

To install guidance from the edited starter, set `CURRENT_WORKSPACE` to the candidate manifest and `GUIDANCE_WORKSPACE` to its directory. Reuse `pale_here` from this page and start at [Review the changes](https://rawthoughts.in/pale/materialize-repository-guidance/#save-the-plan-before-changing-repositories) to make a new guidance plan. For a runtime workspace, follow the [file-plan instructions](https://docs.rawthoughts.in/pale/workspace#check-plan-and-apply) using the candidate.

<a id="editor-support"></a>

## Editor support

Use the [VS Code setup guide](https://docs.rawthoughts.in/pale/integrations/vscode#run-the-extension-locally) to connect the extension to its language server. The small example there demonstrates the editor connection. Open your configured workspace for the full profile.

Use **Pale: Select Profile Context**, then open **Pale Profile** in the Explorer. The language server can point to problems and take you to the declaration behind a result. Configuration review uses the files as they appear in the editor, including unsaved edits.

Return to [Introduction to Pale](https://rawthoughts.in/pale/understand-your-world/) for the broader product, or continue with [repository guidance](https://rawthoughts.in/pale/materialize-repository-guidance/).


Reading path: [Pale](https://rawthoughts.in/pale/) > [Inspect your workspace](https://rawthoughts.in/pale/inspect-your-workspace/)


Source code for [Pale](https://github.com/getHarshOnline/pale) is credited to [Harsh Joshi](https://getharsh.in/about/).
