## Minishell
### About the 42 Norm:
- Each file must contain no more than 5 functions.
- Each function must not exceed 25 lines.
- The project must be written solely in C.
- Only one global variable is allowed.
- Any crash, leak, or conditional jump is forbidden.
- Allowed external functions are: `readline`, `rl_clear_history`, `rl_on_new_line`,
                                  `rl_replace_line`, `rl_redisplay`, `add_history`,
                                  `printf`, `malloc`, `free`, `write`, `access`, `open`, `read`,
                                  `close`, `fork`, `wait`, `waitpid`, `wait3`, `wait4`, `signal`,
                                  `sigaction`, `sigemptyset`, `sigaddset`, `kill`, `exit`,
                                  `getcwd`, `chdir`, `stat`, `lstat`, `fstat`, `unlink`, `execve`,
                                  `dup`, `dup2`, `pipe`, `opendir`, `readdir`, `closedir`,
                                  `strerror`, `perror`, `isatty`, `ttyname`, `ttyslot`, `ioctl`,
                                  `getenv`, `tcsetattr`, `tcgetattr`, `tgetent`, `tgetflag`,
                                  `tgetnum`, `tgetstr`, `tgoto`, `tputs`.

### Project Overview:
This project aims to create **our own shell** from scratch, taking bash as a reference. It is the first real challenge 42 offers in the first months of school, as it is expected to take around **200 hours** to complete.

Our program:
- displays a **prompt** waiting for a new command to be executed, with a **working history**
- handles single and double **quoting**
- supports **redirections** (<, <<, >, >>), **pipes**, **wildcards**, **parenthensis** and **logical operators** (&&, ||)
- allows the usage of **environment variables**
- reacts to **signals** (Ctrl + C, Ctrl + D, Ctrl + \\)
- implements the following **built-ins** and their subtleties : `echo`, `cd`, `pwd`, `export`, `unset`, `env`, `exit`
- keeps track of the last **exit code**

This was a group project with my teammate [bvasseur](https://github.com/basilounet), and we divided our work as the following :
- prompting, expansion and execution were made by bvasseur
- lexing/parsing, signals, wildcards and built-ins were my part

Both the parsing and the execution are done **recursively**, which allows our shell to handle deeply nested commands such as `((((((((cat a) | cat -e && cat a) | cat -e && cat a)...`.

What makes our project complete is the **inheritance** of infiles and outfiles within brackets like `(((cat < a < b) > c) | cat -e) > d << e`, which follows the exact bash rules.

A few additions were also implemented such as the stylized prompt, the BASE environment variable, the expansion in heredocs, or the advanced cd with `-` argument and CDPATH.

## Preview:

Some examples of commands using our shell.

![image](https://github.com/user-attachments/assets/88a461e1-d4f1-456a-b11f-13677fe02bf9)
