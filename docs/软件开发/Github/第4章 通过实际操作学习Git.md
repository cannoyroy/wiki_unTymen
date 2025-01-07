# 第4章 通过实际操作学习Git

## 4.1 基本操作

### git init——初始化仓库

```bash
$ git init
Initialized empty Git repository in /Users/hirocaster/github/github-book
```

如果初始化成功，执行了 git init命令的目录下就会生成 .git 目录。这个 .git 目录里存储着管理当前目录内容所需的仓库数据。

> 这个目录是隐藏起来的。Mac可以通过**CMD+SHIFT+.**来显示隐藏文件

在 Git 中，我们将这个目录的内容称为“附属于该仓库的工作树”。文件的编辑等操作在工作树中进行，然后记录到仓库中，以此管理文件的历史快照。如果想将文件恢复到原先的状态，可以从仓库中调取之前的快照，在工作树中打开。开发者可以通过这种方式获取以往的文件。

### git status——查看仓库的状态

```bash
$ git status
# On branch master
# Initial commit
nothing to commit (create/copy files and use "git add" to track)
```

结果显示了我们当前正处于 master 分支下。接着还显示了没有可提交的内容。所谓提交（Commit），是指“记录工作树中所有文件的当前状态”。

尚没有可提交的内容，就是说当前我们建立的这个仓库中还没有记录任何文件的任何状态。这里，我们建立 README.md 文件作为管理对象，为第一次提交做前期准备。

```bash
$ touch README.md
$ git status
# On branch master
#
(use "git add <file>..." to include in what will
# Initial commit
### Untracked files:# be committed)#
# README.md
nothing added to commit but untracked files present (use "git add" to
track)
```
### git add——向暂存区中添加文件

如果只是用 Git 仓库的工作树创建了文件，那么该文件并不会被记入 Git 仓库的版本管理对象当中。因此我们用 git status命令查看README.md 文件时，它会显示在 Untracked files 里。

要想让文件成为 Git 仓库的管理对象，就需要用 git add命令将其加入暂存区（Stage 或者 Index）中。暂存区是提交之前的一个临时区域。

```bash
$ git add README.md
$ git status
# On branch master
# Initial commit
# Changes to be committed:
# (use "git rm --cached <file>..." to unstage)
#
# new file: README.md
```

### git commit——保存仓库的历史记录

git commit命令可以将当前暂存区中的文件实际保存到仓库的历史记录中。通过这些记录，我们就可以在工作树中复原文件。

- ……记述一行提交信息

```bash
$ git commit -m "First commit"
[master (root-commit) 9f129ba] First commit
1 file changed, 0 insertions(+), 0 deletions(-)
create mode 100644 README.md
```

-m参数后的 "First commit"称作提交信息，是对这个提交的概述。

- ……记述详细提交信息

刚才我们只简洁地记述了一行提交信息，如果想要记述得更加详细，请不加 -m，直接执行 git commit命令。执行后编辑器就会启动，并显示如下结果。

```bash
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
#
# Initial commit
#
# Changes to be committed:
# (use "git rm --cached <file>..." to unstage)
#
# new file: README.md
#
```

在编辑器中记述提交信息的格式如下：

- 第一行：用一行文字简述提交的更改内
- 第二行：空行
- 第三行以后：记述更改的原因和详细内容

只要按照上面的格式输入，今后便可以通过确认日志的命令或工具看到这些记录。

在以 #（井号）标为注释的 Changes to be committed（要提交的更改）栏中，可以查看本次提交中包含的文件。将提交信息按格式记述完毕后，请保存并关闭编辑器，以 #（井号）标为注释的行不必删除。随后，刚才记述的提交信息就会被提交。

> Vim编辑器中，

- ……中止提交

  如果在编辑器启动后想中止提交，请将提交信息留空并直接关闭编辑器，随后提交就会被中止。

- ……

- 查看提交后的状态

  执行完 git commit命令后再来查看当前状态。

  ```bash
  $ git status
  # On branch master
  nothing to commit, working directory clean
  ```

  当前工作树处于刚刚完成提交的最新状态，所以结果显示没有更改。

### git log——查看提交日志

commit 栏旁边显示的“9f129b……”是指向这个提交的哈希值。Git 的其他命令中，在指向提交时会用到这个哈希值。

Author 栏中显示我们给 Git 设置的用户名和邮箱地址。Date 栏中显示提交执行的日期和时间。再往下就是该提交的提交信息。

- ……只显示提交信息的第一行

  ```bash
  --pretty=short
  ```

- ……只显示指定目录、文件的日志

  只要在 git log命令后加上目录名，便会只显示该目录下的日志。

  如果加的是文件名，就会只显示与该文件相关的日志。

- ……显示文件的改动

  如果想查看提交所带来的改动，可以加上 -p参数，文件的前后差别就会显示在提交信息之后。

### git diff——查看更改前后的差别

git diff命令可以查看工作树、暂存区、最新提交之间的差别。单从字面上可能很难理解，各位不妨跟着笔者的解说亲手试一试。

当我们在刚刚提交的 README.md 中写点东西……

- ……查看工作树和暂存区的差别

```bash
$ git diff
diff --git a/README.md b/README.md
index e69de29..cb5dc9f 100644
--- a/README.md
+++ b/README.md
@@ -0,0 +1 @@
+# README
```

由于我们尚未用 git add命令向暂存区添加任何东西，所以程序只会显示工作树与最新提交状态之间的差别。

这里解释一下显示的内容。“+”号标出的是新添加的行，被删除的行则用“-”号标出。我们可以看到，这次只添加了一行。

用 git add命令将 README.md 文件加入暂存区。

```bash
$ git add README.md
```

- ……查看工作树和最新提交的差别

如果现在执行 git diff命令，由于工作树和暂存区的状态并无差别，结果什么都不会显示。要查看与最新提交的差别，请执行以下命令。

```bash
$ git diff HEAD
diff --git a/README.md b/README.md
index e69de29..cb5dc9f 100644
--- a/README.md
+++ b/README.md
@@ -0,0 +1 @@
+# README
```

不妨养成这样一个好习惯：在执行 git commit命令之前先执行git diff HEAD命令，查看本次提交与上次提交之间有什么差别，等确认完毕后再进行提交。这里的 HEAD 是指向当前分支中最新一次提交的指针。

## Linux补充-`touch`

`touch` 是一个常见的 Unix/Linux 命令，用于 **创建空文件** 或 **更新文件的时间戳**。它的基本功能是与文件的访问和修改时间相关，常用于文件的管理和操作。

#### 1. **创建文件**

  如果指定的文件不存在，`touch` 会创建一个空的文件。该文件会有一个默认的大小（通常是 0 字节），并且文件的内容是空的。

  **示例：**

  ```bash
touch example.txt
  ```

  - 如果 `example.txt` 文件不存在，`touch` 将创建一个新的空文件。
  - 如果文件已存在，`touch` 不会改变文件内容，只会更新文件的时间戳。

#### 2. **更新文件的时间戳**

  `touch` 还可以用于更新文件的访问时间（`atime`）和修改时间（`mtime`）到当前时间。该命令不会改变文件内容，仅修改文件的时间信息。

  **示例：**

  ```bash
touch example.txt
  ```

  - 如果 `example.txt` 已存在，执行后会更新该文件的修改时间和访问时间为当前时间。
  - 如果文件不存在，则创建一个新的空文件。

#### 3. **选项**

  `touch` 命令还支持多个选项来控制其行为。

  - **`-c`** 或 **`--no-create`**：如果文件不存在，不创建文件，仅更新已有文件的时间戳。

    ```bash
    touch -c example.txt
    ```

  - **`-t`**：允许你手动设置时间戳，而不是使用当前时间。你需要指定一个特定的时间格式。

    ```bash
    touch -t 202312251230 example.txt
    ```

    这会将 `example.txt` 的时间戳设置为 2023 年 12 月 25 日 12:30。

  - **`-d`** 或 **`--date`**：使用指定的日期和时间设置文件的时间戳。

    ```bash
    touch -d "2023-12-25 12:30" example.txt
    ```

    这将文件 `example.txt` 的时间戳设置为给定的日期和时间。

  - **`-r`**：根据另一个文件的时间戳来设置目标文件的时间戳。

    ```bash
    touch -r reference.txt target.txt
    ```

    这会将 `target.txt` 的时间戳设置为 `reference.txt` 的时间戳。

#### 4. **使用场景**

  - **创建空文件**：用于快速创建一个空的文件，特别是在编写脚本或初始化项目时。例如，创建一个 `README.md` 文件，初始化一个日志文件等。

  - **更新文件时间戳**：在某些版本控制系统（如 Git）中，`touch` 可以用于更新文件的时间戳，使其被认为是最近修改的，从而触发后续的操作。

  - **批量操作**：可以在批量操作中通过 `touch` 更新多个文件的时间戳。例如，在多个文件上执行时间戳更新操作，而不更改文件内容。

#### 5. **总结**

  `touch` 是一个简单却强大的命令，通常用于以下两种场景：

  - **创建空文件**，如果指定文件不存在。
  - **更新文件时间戳**，而不修改文件内容。

  通过其各种选项，`touch` 可以灵活地应用于不同的文件管理任务。
