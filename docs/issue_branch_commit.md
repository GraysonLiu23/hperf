# hperf开发文档：工单、分支与提交

hperf开发主要依托Gitea代码托管平台进行，为了方便后续协作，提出以下开发流程的建议。

## 工单（issue）

在开发一个新功能前，在Gitea上撰写一个工单。

工单的标题简要说明需要开发的功能，内容可以是对需要开发功能的说明、实现的思路、以及记录开发过程中的问题等，内容可以自由发挥。

工单创建后，会生成一个工单ID，其格式为 `SOLE/hperf#XX` ，该ID能够在commit中引用，这样commit时，直接引用该工单说明本次commit是为了开发这一个工单描述的内容，并且Gitea的工单界面能够关联到该提交，方便追踪。

## 分支（branch）

通常，分支关联工单，如果工单是为了开发一个新功能，应当为这个工单新建一个分支，并且分支应当与工单有对应关系。

例如，工单ID为 `SOLE/hperf#6` ，为了开发该工单描述的功能，应当在最新的master分支上建立一个分支，名为 `feature-#6`，将该分支推送到Gitea后，在Gitea该工单的页面，点击右侧“分支/标记未指定”按钮，将该工单与该分支关联起来。

当工单描述的内容已经开发完成后，发出合并请求（merge request），将该分支内容合并到master分支上，同时删除该feature分支，与之关联的工单也随之关闭。

## 提交（commit）

在分支上进行开发时，可按照开发的功能要点多次提交，提交时，需要撰写commit message，一般格式为：

```
<type>: <subject>     // header
                      // 
(other message)       // body
```

其中常用的`<type>`包括：

* 新功能开发：`feat`
* 更新文档：`docs`
* 添加测试：`test`
* bug修复：`fix`
* 调整代码格式：`style`
* 重构代码结构：`refactor`
* 其他不影响代码功能的杂项变动：`chore`

其中主题`<subject>`是这次commit的简短描述，通常可以在这里引用工单ID，方便后续跟踪。

如果`<subject>`描述得不够清楚，可以继续补充body部分的内容，说明代码变更的具体内容，包括变更前后的行为、影响的范围等。