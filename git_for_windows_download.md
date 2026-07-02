# Git for Windows Download

<https://git-scm.com/download/win>

## Git v2.55.0 (2026-06)

Still has the [Ctrl+C exit SSH](https://unix.stackexchange.com/a/689405) bug,
tracked upstream at
[git-for-windows/git#3848](https://github.com/git-for-windows/git/issues/3848).
During install, on the "Choosing the SSH executable" page,
pick **"Use external OpenSSH"** instead of the default "Use bundled OpenSSH" to avoid it.
This needs `C:\Windows\System32\OpenSSH\ssh.exe` to exist
(System settings > Optional features > View features > OpenSSH Client).
On my machine it was already present and working,
probably enabled by default.

<https://github.com/git-for-windows/git/releases/download/v2.55.0.windows.1/Git-2.55.0-64-bit.exe>

## Git v2.34.1 (2021-11)

Newer versions have problem: [Ctrl+C exit SSH](https://unix.stackexchange.com/a/689405)

<https://github.com/git-for-windows/git/releases/download/v2.34.1.windows.1/Git-2.34.1-64-bit.exe>

## Git LFS

GitHub blocks files larger than 100 MiB.
To track files beyond this limit, use Git Large File Storage (Git LFS).

Example commands:

```sh
git lfs install

git lfs track --filename CALD3_installer_d201411.zip  # this creates file ".gitattributes"
```

### Documentation

- <https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github#file-size-limits>
- <https://git-lfs.com/>

