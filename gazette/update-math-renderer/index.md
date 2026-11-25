Title: Update the math renderer

[Read HTML](https://rawthoughts.in/gazette/update-math-renderer/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="update-the-math-renderer"></a>

# Update the math renderer

If Gazette stops typesetting after you replace Node or update the math adapter, rebuild its settings and reuse your [math-enabled Field Notes request](https://rawthoughts.in/gazette/typeset-mathematics/).

<a id="keep-the-old-settings-and-request"></a>

## Keep the old settings and request

Stop the preview with **Ctrl+D**. Set `GAZETTE_REQUEST` to the request you last used. The helper requires fresh paths for both files. These commands back up the old files and copy the current request before generating replacements:

```sh
(
  set -e
  cd "$GAZETTE_PUBLICATION"
  gazette_math_recovery_dir=$(mktemp -d "$GAZETTE_PUBLICATION/math-recovery.XXXXXX")
  printf 'Backup directory: %s\n' "$gazette_math_recovery_dir"
  cp "$GAZETTE_REQUEST" "$gazette_math_recovery_dir/current-request.json"
  mv math-runtime.toml "$gazette_math_recovery_dir/math-runtime.toml"
  mv preview-math-request.json "$gazette_math_recovery_dir/preview-math-request.json"
  gazette_math_node=$(node -p 'process.execPath')
  python3 "$GAZETTE_SOURCE/examples/first-publication/configure_math.py" \
    --gazette-source "$GAZETTE_SOURCE" \
    --request "$gazette_math_recovery_dir/current-request.json" \
    --node "$gazette_math_node"
)
```

**Warning**

**If a command fails, read the error and look in the printed backup directory before trying again.**

The new `math-runtime.toml` records your current Node executable. The new request keeps your workspace and sites, and resets `math_generation` to the [default limits](https://rawthoughts.in/gazette/typeset-mathematics/#select-the-local-interpreter-and-producer). If you changed those limits, copy the values you still need from the backup. Keep the include and Markdown profile in `gazette.toml`.

<a id="restart-with-the-new-settings"></a>

## Restart with the new settings

Start the preview with the new request. If it includes the workbook, keep `--listen site:workbook=127.0.0.1:0` as well:

```sh
export GAZETTE_REQUEST="$GAZETTE_PUBLICATION/preview-math-request.json"
cat "$GAZETTE_REQUEST" - | "$GAZETTE" preview-sites \
  --local --allow-listeners --local-urls --watch \
  --listen site:field-notes=127.0.0.1:0
```

Open the new preview URL and check the [inline equation and displayed fraction](https://rawthoughts.in/gazette/typeset-mathematics/#write-and-preview-the-calculation). Keep this request for later edits.


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Update the math renderer](https://rawthoughts.in/gazette/update-math-renderer/)


Source code for [Gazette](https://github.com/getHarshOnline/gazette) is credited to [Harsh Joshi](https://getharsh.in/about/).
