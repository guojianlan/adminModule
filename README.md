# admin modules

## 所有的关系表
用户表  
角色表  
权限表  
菜单表  
用户角色表  
角色权限表  
角色菜单表
---
## 创建所有的表
```mysql-psql
# 用户表
CREATE TABLE `admin_user` (
  `id` int NOT NULL AUTO_INCREMENT,
  `ctime` int NOT NULL DEFAULT '0',
  `mtime` int NOT NULL DEFAULT '0',
  `dtime` int NOT NULL DEFAULT '0',
  `mobile` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
  `email` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
  `password` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
  `is_super` tinyint NOT NULL DEFAULT '0',
  PRIMARY KEY (`id`),
  KEY `Imobile` (`mobile`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
# 角色表
CREATE TABLE `admin_role` (
  `id` int NOT NULL AUTO_INCREMENT,
  `ctime` int NOT NULL DEFAULT '0',
  `mtime` int NOT NULL DEFAULT '0',
  `dtime` int NOT NULL DEFAULT '0',
  `name` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `description` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
# 权限表
CREATE TABLE `admin_permission` (
  `id` int NOT NULL AUTO_INCREMENT,
  `ctime` int NOT NULL DEFAULT '0',
  `mtime` int NOT NULL DEFAULT '0',
  `dtime` int NOT NULL DEFAULT '0',
  `name` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `method` enum('get','post','put','delete') COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'get' COMMENT 'url方法',
  `uri` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '请求的url',
  `description` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
# 菜单表
CREATE TABLE `admin_menu` (
  `id` int NOT NULL AUTO_INCREMENT,
  `ctime` int NOT NULL DEFAULT '0',
  `mtime` int NOT NULL DEFAULT '0',
  `dtime` int NOT NULL DEFAULT '0',
  `name` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `url` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `description` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
# 用户角色表
CREATE TABLE `admin_user_role` (
  `id` int NOT NULL AUTO_INCREMENT,
  `ctime` int NOT NULL DEFAULT '0',
  `mtime` int NOT NULL DEFAULT '0',
  `dtime` int NOT NULL DEFAULT '0',
  `user_id` int NOT NULL,
  `role_id` int NOT NULL,
  PRIMARY KEY (`id`),
  KEY `Iuser_id` (`user_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

# 角色权限表
CREATE TABLE `admin_role_permission` (
  `id` int NOT NULL AUTO_INCREMENT,
  `ctime` int NOT NULL DEFAULT '0',
  `mtime` int NOT NULL DEFAULT '0',
  `dtime` int NOT NULL DEFAULT '0',
  `role_id` int NOT NULL,
  `permission_id` int NOT NULL,
  PRIMARY KEY (`id`),
  KEY `Irole_id` (`role_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

# 角色菜单表
CREATE TABLE `admin_role_menu` (
  `id` int NOT NULL AUTO_INCREMENT,
  `ctime` int NOT NULL DEFAULT '0',
  `mtime` int NOT NULL DEFAULT '0',
  `dtime` int NOT NULL DEFAULT '0',
  `role_id` int NOT NULL,
  `menu_id` int NOT NULL,
  PRIMARY KEY (`id`),
  KEY `Irole_id` (`role_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```
