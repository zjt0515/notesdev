```sql
CREATE DATABASE flight;
use flight;
```

flight

```sql
SET FOREIGN_KEY_CHECKS=0;
DROP TABLE IF EXISTS `flight`;
CREATE TABLE `flight` (
  `f_id` char(8) NOT NULL,
  `f_src` varchar(15) DEFAULT NULL,
  `f_des` varchar(15) DEFAULT NULL,
  `f_date` date NOT NULL,
  `f_start_time` char(6) DEFAULT NULL,
  `f_end_time` char(6) DEFAULT NULL,
  `f_fares` float(8,0) DEFAULT NULL,
  `f_discount_nums` float(8,0) DEFAULT NULL,
`f_discount` float(8,0) DEFAULT NULL,
`f_remain_seats` int(4) DEFAULT NULL,
  `f_subordinate_company` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`f_id`,`f_date`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `flight` VALUES ('F001', '南京', '兰州', '2022-01-12', '15:30', '17:20', '300', '10', '5','41', '甲公司');
INSERT INTO `flight` VALUES ('F001', '南京', '昆明', '2022-01-22', '15:30', '17:20', '300', 5, '8', '47','乙公司');
INSERT INTO `flight` VALUES ('F001', '南京', '北京', '2022-01-26', '10:30', '12:20', '500', 23, '15, '87','丙公司');
                             
INSERT INTO `flight` (
    `f_id`, `f_src`, `f_des`, `f_date`,
    `f_start_time`, `f_end_time`, `f_fares`,
    `f_discount_nums`, `f_discount`, `f_remain_seats`, `f_subordinate_company`
) VALUES
('CA1234', '北京', '上海', '2025-06-15', '0800', '1000', 800, 20, 0.8, 50, '中国国航'),
('MU5678', '上海', '广州', '2025-06-16', '0900', '1100', 700, 10, 0.85, 60, '东方航空'),
('CZ9012', '广州', '深圳', '2025-06-17', '0700', '0830', 400, 5, 0.9, 30, '南方航空'),
('HU3456', '深圳', '北京', '2025-06-18', '1200', '1500', 900, 15, 0.75, 40, '海南航空'),
('ZH7890', '北京', '成都', '2025-06-19', '1000', '1230', 650, 8, 0.8, 35, '深圳航空');

```

管理员

```sql
SET FOREIGN_KEY_CHECKS=0;
DROP TABLE IF EXISTS `user`;
CREATE TABLE `user` (
  `u_id` varchar(10) NOT NULL,
  `u_username` varchar(40) DEFAULT NULL,
  `u_password` varchar(40) DEFAULT NULL,
  PRIMARY KEY (`u_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `user` VALUES ('B22040515', 'zjt', '123456');

```
