# ORM

## 数据库配置

https://hub.docker.com/

https://hub.docker.com/_/mysql



```yaml
# Use root/example as user/password credentials
services:
  db:
    image: mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: 123456
    # (this is just an example, not intended to be a production configuration)
    ports:
      - 3308:3308
  adminer:
    image: adminer
    restart: always
    ports:
      - 8080:8080
```



```bash
docker compose up
```

命令行传参

`npx cross-env DB_PASS=654321 pnpm start:dev`

![image-20250603210623443](./images/image-20250603210623443.png)

## ORM、ORM工具库

> Object Relation Mapping 面向对象映射
> 将面向对象的概念和数据库中的概念对应
>
> 对象对应着一张表，对象的一个实例对应表中的一条记录
>
> 1. 方便维护，数据模型定义在同一个地方
> 2. 代码量少，对接多种数据库
> 3. 工具多、自动化能力强
> 4. 不利于sql优化
>
> ORM库：
>
> 1. sequelize
> 2. knex
> 3. typeorm
> 4. prisma



## TypeORM

文档：https://typeorm.bootcss.com/

https://github.com/typeorm/typeorm

> ts >=4.5

```bash
pnpm add @nestjs/typeorm typeorm reflect-metadata mysql2
pnpm add @types/node -D
// db driver
pnpm install mysql2
```

```ts
// app.ts
import "reflect-metadata"
```

```json
// tsconfig.json
"emitDecoratorMetadata": true,
"experimentalDecorators": true,
```

