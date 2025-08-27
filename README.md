zsh Action
==========


This GitHub Action executes commands in a properly initialized ZSh environment, automatically sourcing your `.zshrc` file.

## Usage

```yaml
- name: Run commands in zsh
  uses: gbraad-actions/zsh-action@main
  with:
    run: |
      # Your zsh commands here
      echo "zsh version: $(zsh --version)"
      # Functions from .zshrc are available
      if type devenv >/dev/null 2>&1; then
        devenv dotfedora exec cat /etc/os-release
      fi
    as_user: runner
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `run` | Commands to run in ZSh | Yes | N/A |
| `as_user` | User to run the commands as | No | "" |

## Outputs

| Output | Description |
|--------|-------------|
| `exit_code` | The exit code of the commands |


> [!NOTE]
> - Ensure your `.zshrc` is configured correctly for non-interactive shells.
> - This action sources the commands which has side effects for back-ticks
