# 安装与配置
!> 本帮助文档基于最新版本的 **RPGItems** 所写。各类命令与系统机制可能会发生变化并且不再适用于旧版本。

**RPGItems-reborn** 无需依赖任何插件，只需要您的服务端为 Spigot 或其衍生服务端，游戏版本在 `[1.14, 1.21.1]` 区间即可运行，使用最基本的功能。  
同时，RPGItems 可与以下插件联动：

+ [Vault](https://www.spigotmc.org/resources/34315)
+ [WorldEdit](https://dev.bukkit.org/projects/worldedit)
+ [WorldGuard](https://dev.bukkit.org/projects/worldguard)
+ [MythicMobs (4.x/5.x)](https://www.spigotmc.org/resources/5702)
+ [ItemsAdder](https://www.spigotmc.org/resources/73355)
+ [PlaceholderAPI](https://www.spigotmc.org/resources/6245)
+ [ProtocolLib](https://www.spigotmc.org/resources/1997)

在下载完所有必须的 jar 文件后，请将它们放入 `plugins` 文件夹内，并且**重启**服务器。
> 如果您是开发人员，您也可以使用 `PlugManX` 之类的插件管理器，热加载 RPGItems。出于安全考虑，不推荐没有编程能力的人员通过热加载的方式安装本插件。

## 插件语言文本设置

您可能想要修改 RPGItems 的一些文字信息，但编辑这个*似乎是语言文件*的 `zh_CN.template.yml` 却没有任何作用。正如这个文件的文件名所示，这仅仅是一个`模板`。

如果需要修改语言配置，请在插件目录 `/plugins/RPGItems/` 下新建一个配置文件 `语言.custom.yml`，以简体中文为例，新建配置文件 `zh_CN.custom.yml`。  
在模板配置 `zh_CN.template.yml` 中复制您想修改的内容，粘贴到 `zh_CN.custom.yml`，修改，保存，重载配置文件即可。

您在 `语言.custom.yml` 中写入的内容有最高的优先级，插件会优先使用其中的配置，在该配置中无法找到相应的值时，再使用插件 jar 内的 `lang/语言.yml` 配置。

## 插件设置

在使用 **RPGItems** 时插件会默认生成一份配置文件。

在大多数情况下您不需要去修改这个文件，但是配置文件中的部分设置可能会对您有用。

这是一份插件的默认配置文件：

```
language: en_US
version: '1.0'
general:
  readonly: false
  enabled_languages:
  - en_US
  - zh_CN
  give_perms: false
  item:
    fs_lock: false
    show_loaded: false
    item_stack_uuid: true
  reload-notice-readonly-server: true
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
  placeholder_api:
    enable: true
  protocol_lib:
    enable: true
    auto_replace_armor_material_to_netherite_or_diamond: true
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
factor_config:
  __class__: think.rpgitems.data.FactorConfig
  factors:
    creature:
      name: '&eCreature'
      damage_to:
        machine: damage * 0.8
        supernatural: damage * 1.2
    machine:
      name: '&bMachine'
      damage_to:
        creature: damage * 1.2
        supernatural: damage * 0.8
    supernatural:
      name: '&dSuper Natural'
      damage_to:
        creature: damage * 0.8
        machine: damage * 1.2
stone:
  max_count: 3
  shift-right-click-remove-last: false
  allow_triggers:
  - SNEAK
  - LEFT_CLICK
  - RIGHT_CLICK
  - SPRINT
  - SWAP_TO_MAINHAND
  - SWAP_TO_OFFHAND
  - DROP
  - CLICK_BLOCK
  - HIT
  allow_triggers_armour:
  - ANTI_CRITICAL
  - DODGE
  - SNEAK
  - DOUBLE_SNEAK
  - SNEAKING
```
## config 配置文件说明

- `language` 插件使用的语言。默认情况下插件使用的语言为中文 (`zh_CN`)。
- general 设置：
  - `readonly` 是否开启只读模式。 (禁止编辑神器与技能石)
  - `enabled_languages` 可使用的语言。
  - `give_perms` 使用 `/rpgitem give` 时是否需要额外权限。
  - item
    - `fs_lock` 是否保护道具配置文件完整性。在 Windows 服务器中锁定道具配置文件。开启目录重定向之后建议关闭该选项。
    - `show_loaded` 是否在启动时显示载入的文件。
    - `item_stack_uuid` 是否在给予道具时为道具赋予独特的uuid来防止道具堆叠。此项可能会影响 shopkeepers 等经济插件中的道具交易。
  - `items_dir_redirect` items 目录重定向位置，通常配合 readonly 使用，做到多服同步插件列表。
  - `reload-notice-readonly-server` 重载插件时是否通知其它子服重载插件。
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
  - placeholder_api
    - `enable` 是否启用 PlaceholderAPI 插件支持。开启后 Lore 将会替换变量
  - protocol_lib
    - `enable` 是否启用 ProtocolLib 插件支持。开启后神器物品将可以伪装。
    - `auto_replace_armor_material_to_netherite_or_diamond` 是否自动替换神器盔甲套装为合金或钻石套，并伪装成神器设置的物品类型
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
- factor_config 设置
  - factors 元素列表
    - `元素名1`
      - `name` 显示名称
      - `damage_to` 攻击目标元素时的伤害修改设置
        - `目标元素名1` 伤害值表达式，如 `damage * 0.8` 为 80% 伤害
        - `目标元素名2` ... 以此类推
    - `元素名2`
      - ...以此类推
- stone 设置
  - `max_count` 每个神器所能安装的技能石最大数量
  - `shift-right-click-remove-last` 是否允许在物品栏按住Shift+右键点击神器卸下最后一个技能石
  - `allow_triggers` 自定义触发器允许设置的触发器列表 (普通神器)
  - `allow_triggers_armour` 自定义触发器允许设置的触发器列表 (盔甲类型神器)
