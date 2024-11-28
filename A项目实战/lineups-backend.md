## 现有方案

https://valoplant.gg/zh/3W1B6R

https://www.strats.gg/valorant/lineups/1718208290227

## 数据库表

```sql
create table if not exists lineup
(
    id               bigint auto_increment comment 'id' primary key,
    map_id           bigint                             null comment '地图id',
    agent_id         bigint                             null comment '英雄id',
    throw_mode       tinyint                            null comment '投掷方式',
    tags             varchar(1024)                      null comment '标签列表(json数组)',
    effect_image_url varchar(256)                       null comment '效果图',
    place_image_url  varchar(256)                       null comment '站位图',
    aim_image_url    varchar(256)                       null comment '瞄点图',
    favour_num       int      default 0                 not null comment '点赞数',
    notes            text                               null comment '备注',
    author_id        bigint                             not null comment '作者id',

    create_time      datetime default current_timestamp not null comment '创建时间',
    update_time      datetime default current_timestamp not null on update current_timestamp comment '更新时间',
    is_deleted       tinyint  default 0                 not null comment '逻辑删除'
)
    comment '道具点位';
```



```sql
create table if not exists lineup
(
    id               bigint auto_increment comment 'id' primary key,
    map_id           bigint                             null comment '地图id',
    agent_id         bigint                             null comment '英雄id',
    throw_mode       tinyint                            null comment '投掷方式',
    tags             varchar(1024)                      null comment '标签列表(json数组)',
    uses_image  		 varchar(1024)											null comment '使用(json数组)'
    effect_image_url varchar(256)                       null comment '效果图',
    place_image_url  varchar(256)                       null comment '站位图',
    aim_image_url    varchar(256)                       null comment '瞄点图',
    favour_num       int      default 0                 not null comment '点赞数',
    notes            text                               null comment '备注',
    author_id        bigint                             not null comment '作者id',

    create_time      datetime default current_timestamp not null comment '创建时间',
    update_time      datetime default current_timestamp not null on update current_timestamp comment '更新时间',
    is_deleted       tinyint  default 0                 not null comment '逻辑删除'
)
    comment '道具点位';
```

```json
[
  {
    title: '效果图',
    url: '',
    notes: ''
  }
]
```



