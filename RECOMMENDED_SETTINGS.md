# Recommended Bash 5 settings

```bash
#! /usr/bin/env bash

# If possible, add tab completion for many more commands
[ -f /etc/bash_completion ] && source /etc/bash_completion

# If set, a command name that is the name of a directory is executed as if it were the argument to the cd command.
shopt -s autocd

# If this is set, an argument to the cd builtin command that is not a directory is assumed to be the name of a variable
# whose value is the directory to change to.
shopt -s cdable_vars

# If set, minor errors in the spelling of a directory component in a cd command will be corrected. The errors checked
# for are transposed characters, a missing character, and a character too many. If a correction is found, the corrected
# path is printed, and the command proceeds.
shopt -s cdspell

# If this is set, Bash checks that a command found in the hash table exists before trying to execute it. If a hashed
# command no longer exists, a normal path search is performed.
shopt -s checkhash

# If set, Bash checks the window size after each command and, if necessary, updates the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, Bash attempts to save all lines of a multiple-line command in the same history entry. This allows easy
# re-editing of multi-line commands.
shopt -s cmdhist

# If set, Bash replaces directory names with the results of word expansion when performing filename completion. This
# changes the contents of the readline editing buffer. If not set, Bash attempts to preserve what the user typed.
shopt -s direxpand

# If set, Bash attempts spelling correction on directory names during word completion if the directory name initially supplied does not exist.
shopt -s dirspell

# If set, Bash includes filenames beginning with a ‘.’ in the results of filename expansion.
shopt -s dotglob

# If set, aliases are expanded as described below under Aliases, Aliases. This option is enabled by default for interactive shells.
shopt -s expand_aliases

# If set, the extended pattern matching features described above (see Pattern Matching) are enabled.
shopt -s extglob

# If set, the pattern ‘**’ used in a filename expansion context will match all files and zero or more directories and
# subdirectories. If the pattern is followed by a ‘/’, only directories and subdirectories match.
shopt -s globstar

# If set, the history list is appended to the file named by the value of the HISTFILE variable when the shell exits,
# rather than overwriting the file.
#
# If set, and Readline is being used, a user is given the opportunity to re-edit a failed history substitution.
#
# If set, and Readline is being used, the results of history substitution are not immediately passed to the shell
# parser. Instead, the resulting line is loaded into the Readline editing buffer, allowing further modification.
shopt -s histappend histreedit histverify

# If set, and Readline is being used, Bash will attempt to perform hostname completion when a word containing a ‘@’ is
# being completed (see Commands For Completion). This option is enabled by default.
shopt -s hostcomplete

# If set, Bash will send SIGHUP to all jobs when an interactive login shell exits (see Signals).
shopt -s huponexit

# Allow a word beginning with ‘#’ to cause that word and all remaining characters on that line to be ignored in an interactive shell. This option is enabled by default.
shopt -s interactive_comments

# If enabled, and the cmdhist option is enabled, multi-line commands are saved to the history with embedded newlines
# rather than using semicolon separators where possible.
shopt -s lithist

# If set, and Readline is being used, Bash will not attempt to search the PATH for possible completions when completion
# is attempted on an empty line.
shopt -s no_empty_cmd_completion

# If set, Bash matches filenames in a case-insensitive fashion when performing filename expansion.
shopt -s nocaseglob

# If set, Bash matches patterns in a case-insensitive fashion when performing matching while executing case or
# [[ conditional commands.
shopt -s nocasematch

# If set, the source builtin uses the value of PATH to find the directory containing the file supplied as an argument. This option is enabled by default.
shopt -s sourcepath

# Don't want any coredumps.
ulimit -S -c 0
```

