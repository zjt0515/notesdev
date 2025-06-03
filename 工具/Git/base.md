## commit message 规范

1. https://www.conventionalcommits.org/en/v1.0.0/
2. https://heidiliu2020.github.io/git-commit-message/
3. https://juejin.cn/post/6844903793033756680
4. element项目提交规范: https://element-plus.org/zh-CN/guide/commit-examples.html

```
<type>(<scope>): <desc>

[optional body]

[optional footer]
```

示例

```
feat(miniprogram): 增加了小程序模板消息相关功能
chore: upgrade vueuse to 10.11.0
fix(components): [table] shrinked table expanded when modify data

// 有body的示例
feat(api): 添加获取用户详情的接口

添加了 /api/user/detail 路由，用于前端获取用户详细资料。
该接口支持查询参数 ID，并返回标准 JSON。

// 示例footer
// 关联issue
Closes #123
Fixes #456
// 破坏性改动
BREAKING CHANGE: 删除了旧版登录接口 /api/old-login
```

type:

1. feat特性，新功能feature
2. fix 修复bug
3. docs 文档注释
4. style 代码格式
5. refactor重构/优化
6. perf 性能优化
7. test 增加测试
8. chore 构建过程或辅助工具的变动，例如升级
9. revert 回退
10. build 打包

### 相关工具

[`commitlint`](https://github.com/conventional-changelog/commitlint) + [`husky`](https://github.com/typicode/husky)：强制检查 commit 信息

[`cz-cli`](https://github.com/commitizen/cz-cli)：交互式提交消息生成器（Commitizen）

`semantic-release`：自动根据 commit message 生成 changelog 和版本号

## 添加远程仓库

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
// 查看
git remote -v
```



## 推动改动

将master分支推送到名为origin的远程仓库

```bash
git push origin master
```



## 更新与合并

```bash
git pull
```

## 删除

```bash
// 工作区和暂存区删除
git rm a
git rm -r dir
// 相当于
rm a
git add a
// 参数
-f 强制删除

// 暂存区删除
git rm --cached
```

> [!tip]
>
> `--cached`用于取消追踪，在本地工作区保留，远程仓库中删除
