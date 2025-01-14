# 第1章 Github介绍

## 1.1 什么是Github

GitHub 除提供 Git 仓库的托管服务外，还为开发者或团队提供了一系列功能，帮助其高效率、高品质地进行代码编写。

> GitHub 的创始人之一 Chris Wanstrath 曾有个愿望，那就是能有一个Git 仓库的托管服务让自己与朋友轻松分享代码，而这便成为了 GitHub诞生的契机。不过，他也曾经表示：Git 仓库的托管服务是 GitHub 项目的目标之一，这只是漫长路程上的一个点而已。

**GitHub 与 Git 是完全不同的两个东西。**

在 Git 中，开发者将源代码存入名叫“Git 仓库”的资料库中并加以使用。而 GitHub 则是在网络上提供 Git 仓库的一项服务。也就是说，GitHub 上公开的软件源代码全都由 Git 进行管理。理解 Git，是熟练运用 GitHub 的关键所在。

## 1.2 社会化编程

世界上任何人都可以比从前更加容易地获得源代码，将其自由更改并加以公开。如今，世界众多程序员都在通过 GitHub 公开源代码，同时利用 GitHub 支持着自己日常的软件开发。

GitHub 的出现为软件开发者的世界带来了真正意义上的“民主”，让所有人都平等地拥有了更改源代码的权利。这在软件开发领域是一场巨大的革命。而革命领导者 GitHub 的口号便是“社会化编程”。

## 1.3 Github提供的主要功能

- Git仓库

- Organization

  个人使用时只要使用个人账户就足够了，但如果是公司，建议使用 Organization 账户。它的优点在于可以统一管理账户和权限，还能统一支付一些费用。

  如果只使用公开仓库，是可以免费创建 Organization 账户的。因此，如果是以交流群或 IT 小团体的形式进行软件开发时不妨试一试。

- Issue

  Issue 功能，是将一个任务或问题分配给一个 Issue 进行追踪和管理的功能。可以像 BUG 管理系统或 TiDD（Ticket-driven Development）的Ticket 一样使用。在 GitHub 上，每当进行我们即将讲解的 Pull equest，都会同时创建一个 Issue。

  每一个功能更改或修正都对应一个 Issue，讨论或修正都以这个Issue 为中心进行。只要查看 Issue，就能知道和这个更改相关的一切信息，并以此进行管理。

  在 Git 的提交信息中写上 Issue 的 ID（例如“#7”），GitHub 就会自动生成从 Issue 到对应提交的链接。另外，只要按照特定的格式描述提交信息，还可以关闭 Issue。

- Wiki

  通过 Wiki 功能，任何人都能随时对一篇文章进行更改并保存，因此可以多人共同完成一篇文章。

  Wiki 页也是作为 Git 仓库进行管理的，改版的历史记录会被切实保存下来，使用者可以放心改写。由于其支持克隆至本地进行编辑，所以程序员使用时可以不必开启浏览器。

- Pull Request

  开发者向 GitHub 的仓库推送更改或功能添加后，可以通过 Pull Request 功能向别人的仓库提出申请，请求对方合并。

  Pull Request 送出后，目标仓库的管理者等人将能够查看 Pull Request 的内容及其中包含的代码更改。

  同时，GitHub 还提供了对 Pull Request 和源代码前后差别进行讨论的功能。通过此功能，可以以行为单位对源代码添加评论，让程序员之间高效地交流。

  