# HaCasa Nova — Global Area Discovery

This repository contains a customised HaCasa Nova 3.1.0 distribution.

## What changed

HaCasa Nova now separates **area discovery** from **room navigation**:

- Every Home Assistant area is retained in the internal room/entity model.
- The configured Rooms list controls only which areas appear in the room navigation and have room pages.
- Areas hidden from navigation (including areas excluded with `excludeAreas`) still contribute their entities to global views and entity lookups.
- The existing room order, room titles/photos, automatic room selection, and `maxRooms` behaviour are retained.
- The original HaCasa Nova upstream repository is not modified.

This means you can put a camera, sensor, light, lock, or other entity in an area such as **Side** without adding Side as a room page. Its entities remain available to HaCasa Nova's global features.

## Install

Download [hacasa-nova-areas.js](https://raw.githubusercontent.com/graduatingtangerine/testCasava/main/hacasa-nova-areas.js).

For a manual Home Assistant install:

1. Copy the file to `/config/www/hacasa-nova/hacasa-nova-areas.js`.
2. In your `panel_custom:` configuration, point `module_url` to `/local/hacasa-nova/hacasa-nova-areas.js`.
3. If you use `frontend.extra_module_url` for the HaCasa icon, point that entry to the same local file.
4. Restart Home Assistant and hard-refresh the browser.

Example:

```yaml
frontend:
  extra_module_url:
    - /local/hacasa-nova/hacasa-nova-areas.js

panel_custom:
  - name: hacasa-nova
    url_path: hacasa
    sidebar_title: HaCasa
    sidebar_icon: hacasa:logo
    module_url: /local/hacasa-nova/hacasa-nova-areas.js
```

Keep your existing HaCasa settings; the change does not require resetting them.

## Upstream

Based on [damianeickhoff/HaCasa](https://github.com/damianeickhoff/HaCasa), distributed under its MIT license. This repository contains the customised built distribution only.
