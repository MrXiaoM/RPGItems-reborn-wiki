# 安装与配置
!> 本帮助文档基于最新版本的 **RPGItems** 所写。各类命令与系统机制可能会发生变化并且不再适用于旧版本。

**RPGItems-reborn** 无需依赖任何插件，只需要您的服务端为 Paper 或其衍生服务端，游戏版本在 `[1.17, 1.20.4]` 区间。  
同时，RPGItems 可与以下插件联动：

+ [Vault](https://www.spigotmc.org/resources/34315)
+ [WorldEdit](https://dev.bukkit.org/projects/worldedit)
+ [WorldGuard](https://dev.bukkit.org/projects/worldguard)
+ [MythicMobs (5.x)](https://www.spigotmc.org/resources/5702)
+ [ItemsAdder](https://www.spigotmc.org/resources/73355)
+ [PlaceholderAPI](https://www.spigotmc.org/resources/6245)

在下载完所有必须的 jar 文件后，请将它们放入 `plugins` 文件夹内，并且**重启**服务器。
> 如果您是开发人员，您也可以使用 `PlugManX` 之类的插件管理器，热加载 RPGItems，出于安全考虑，不推荐没有编程能力的人员通过热加载的方式安装本插件。

# 插件设置

> 以下信息等待更新

在使用 **RPGItems** 时插件会默认生成一份配置文件。

在大多数情况下您不需要去修改这个文件，但是配置文件中的部分设置可能会对您有用。

这是一份插件的默认配置文件：

```
language: en_US
version: '1.0'
general:
  enabled_languages:
  - en_US
  - zh_CN
  give_perms: false
  item:
    fs_lock: true
    show_loaded: false
    item_stack_uuid: true
command:
  list:
    item_per_page: 9
    power_per_page: 5
support:
  world_guard:
    enable: true
    force_refresh: false
    disable_in_no_pvp: true
    show_warning: true
gist:
  token: ''
  publish: true
item:
  defaults:
    numeric_bar: false
    force_bar: false
    license: All Right Reserved
    enchant_mode: DISALLOW
    allow_anvil_enchant: true
unused:
  locale_inv: false

```
## config 配置文件说明

- language 插件使用的语言。默认情况下插件使用的语言为英文，如果需要使用中文，请将 `language: en_US` 改为 `language: zh_CN` 。
- general 设置：
  - `enabled_languages` 可使用的语言。
  - `give_perms` 使用 `/rpgitem give` 时是否需要额外权限。
  - item
    - `fs_lock` 请勿修改此项。是否保护道具配置文件完整性。在 Windows 服务器中锁定道具配置文件。
    - `show_loaded` 是否在启动时显示载入的文件。
    - `item_stack_uuid` 是否在给予道具时为道具赋予独特的uuid来防止道具堆叠。此项可能会影响 shopkeepers 等经济插件中的道具交易。
- command 设置
  - list 
    - `item_per_page` 使用 `/rpgitem list` 命令时每页列出的道具量。
    - `power_per_page` 使用 `/rpgitem power list` 命令时每页列出的技能数。
- support 设置
  - world_guard
    - `enable` 是否启用 Worldguard 插件支持。
    - `force_refresh` 是否在玩家使用物品时强制刷新 WorldGuard 保护区。仅当遇到WorldGuard相关问题时启用。
    - `disable_in_no_pvp` 是否在非PVP区域禁用 RPGItems 。
    - `show_warning` 当玩家在非PVP区域使用 RPGItems 时是否发送警告。
- gist 设置
  - `token`
  - `publish` 
- item 设置
  - default 制作道具时的默认生效配置。
    - `numeric_bar` 是否默认使用数字显示耐久度。
    - `force_bar` 是否默认显示耐久度。
    - `license` 默认的许可文本。该文本将在物品配置被他人导入时显示。
    - `enchant_mode` 道具附魔模式。
      - `DISALLOW` 禁止附魔。
      - `PERMISSION` 需要拥有 `rpgitem.enchant.[item_name]` 权限后才可附魔。
      - `ALLOW` 无需权限，允许附魔。
    - `allow_anvil_enchant` 是否允许通过铁砧附魔。
    
