

## 项目初始化

https://pnpm.io/zh/pnpm-workspace_yaml

项目架构：https://monorepo.tools/

```yaml
packages:
  - 'examples'
  - 'docs'
  - 'packages/*'
```



```
pnpm install @voxel-ui/components -w
pnpm install @voxel-ui/hook -w
pnpm install @voxel-ui/utils -w
```

## 项目架构

1. components组件
2. hook
3. theme
4. utils
