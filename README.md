# Windo 1.0.0 for Windows x64

Windo is a command-line tool for inspecting and automating a Windows desktop.
Its goal is to make repeatable desktop tasks expressible as direct commands or
readable UTF-8 `.windo` scripts. A script can observe windows and controls,
wait for a condition, act on the desktop, and report the result. The installer
includes offline documentation, examples, language catalogs, and an optional
syntax-highlighting definition for Notepad++.

## What you can do with Windo

- Inspect windows, monitors, pixels, processes, and UI Automation elements;
  produce text or JSON output for selected inspection commands.
- Activate and arrange windows; send keyboard and mouse input; capture parts
  of the desktop and display notifications.
- Wait for windows, files, clipboard changes, processes, or UI elements instead
  of relying on fixed delays. Run long-lived file watchers from the system tray.
- Work with files, directories, clipboard data, INI files, the registry,
  startup entries, processes, and TCP/UDP connections.
- Use variables, conditions, loops, functions, included libraries, retries,
  and error handling to organize scripts.
- Automate Excel and Word through OLE when those applications are installed.
  Separate static commands inspect VBA, Excel 4.0/XLM, and legacy WordBasic
  indicators without starting Office or executing macros.

Windo runs on Windows 10 or 11 x64. It is a console program; interactive
desktop commands run in the current user's desktop session. Review a script
before executing commands that change files, processes, or system settings.

## Install and get started

1. Download and run `Windo-Setup-1.0.0-Win64.exe`.
2. Read and accept the license. Installation for the current user is the
   default; the wizard also offers an all-users installation.
3. Open **Windo Command Prompt** from the Start menu. Its working directory is
   the Windo installation folder, so the installed examples can be used by
   relative path.

```text
Windo.exe help
Windo.exe help watchfiles
Windo.exe --check "Examples\03-desktop-layout.windo"
Windo.exe --file "Examples\03-desktop-layout.windo"
```

`--check` parses a script, checks its block structure, command names, selected
options, and includes without performing its actions. It cannot confirm that
every option, target window, or referenced file will work at runtime. Use
`--file` to execute a UTF-8 script; put arguments for that script after `--`.
The installer associates `.windo` files with Windo when no default handler is
already selected. Adding Windo to `PATH` is optional and off by default; open
a new terminal after enabling it.

## Installed documentation and files

| Installed path | Purpose |
| --- | --- |
| `Windo.exe` | Command-line interpreter and built-in `help` command. |
| `Help\Windo.chm` | English offline user guide with a contents tree, index, guided workflows, and command examples. |
| `Help\Windo-it.chm` | Italian edition of the offline user guide. |
| `Help\AI_SCRIPTING.md` | English scripting reference for people and AI assistants, including language rules and the complete command catalog. |
| `Help\Localization.md` | Instructions for choosing a UI language and translating a catalog. |
| `Examples\` | Ready-to-adapt `.windo` scripts and an examples guide. |
| `locales\en-US.json`, `locales\it-IT.json` | English and Italian runtime message and help catalogs. |
| `NotepadPP\Windo.xml` | Notepad++ User Defined Language for `.windo` syntax highlighting. |
| `NotepadPP\README-en.txt`, `NotepadPP\README-it.txt` | English and Italian instructions for importing the Notepad++ definition. |

The CHM guides are separate files; changing the runtime language does not
switch the guide you open. The Start menu has shortcuts to both guides and
the Examples folder.

### Using `AI_SCRIPTING.md`

Open `Help\AI_SCRIPTING.md` when you need precise script syntax or a command's
arguments. It explains quoting, variables, control flow, error handling, and
the command catalog. You can also provide this file to an external AI
assistant as a reference and ask it to use only documented Windo commands.
Save the proposed script as UTF-8 with a `.windo` extension, inspect actions
that could change your system, run `Windo.exe --check script.windo`, and then
run it with `Windo.exe --file script.windo`. Windo does not require an AI
service to run scripts; the Markdown file is documentation, not an AI engine.

### Using the Notepad++ syntax file

The installer places `Windo.xml` in `NotepadPP` but does not change your
Notepad++ settings. In Notepad++, open **Language > User Defined Language >
Define Your Language**, choose **Import**, and select the installed
`NotepadPP\Windo.xml`. Reopen any `.windo` file already open in the editor.
The definition colors commands, options, strings, and comments, and supports
folding parenthesized blocks. It does not validate or execute scripts; use
Windo's `--check` command for validation. The two README files in `NotepadPP`
give the import steps in English and Italian. Its colors are intended for a
light editor theme and can be adjusted in Notepad++.

### Runtime language files

Windo selects a matching catalog for the Windows display language and falls
back to English when one is unavailable. Set `WINDO_LANG` before launching
Windo to override the selection, for example `set WINDO_LANG=it-IT` in Command
Prompt. To add a translation, copy `locales\en-US.json` to a BCP 47 filename
such as `locales\fr-FR.json`, translate values while preserving keys and
placeholders, and follow `Help\Localization.md`. These JSON files affect
runtime text and command help, not the language of the CHM guides.

## Verify the download and license

`SHA256.TXT` lists the SHA-256 hashes of the installer, `Windo.exe`, and both
CHM guides. To check the downloaded installer in PowerShell, run:

```powershell
Get-FileHash .\Windo-Setup-1.0.0-Win64.exe -Algorithm SHA256
```

Compare the displayed hash with the installer line in `SHA256.TXT`. The other
three hashes can be checked against the corresponding files after installation.

Windo is distributed by Paolo Monti for non-commercial use under `LICENSE.TXT`.
Commercial use requires a separate written agreement with the author. The
installer requires license acceptance; unattended installation must pass
`/ACCEPTLICENSE=YES`.
