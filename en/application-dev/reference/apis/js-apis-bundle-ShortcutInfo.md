# ShortcutInfo

The **ShortcutInfo** module provides shortcut information defined in the configuration file.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## ShortcutWant

Describes the information about the target to which the shortcut points.

**System capability**: SystemCapability.BundleManager.BundleFramework

| Name                     | Type  | Readable| Writable| Description                |
| ------------------------- | ------ | ---- | ---- | -------------------- |
| targetBundle              | string | Yes  | No  | Target bundle of the shortcut.|
| targetModule<sup>9+</sup> | string | Yes  | No  | Target module of the shortcut.  |
| targetClass               | string | Yes  | No  | Target class required by the shortcut.|

## ShortcutInfo

Describes the shortcut attribute information.

**System capability**: SystemCapability.BundleManager.BundleFramework

| Name                   | Type                                      | Readable| Writable| Description                        |
| ----------------------- | ------------------------------------------ | ---- | ---- | ---------------------------- |
| id                      | string                                     | Yes  | No  | ID of the application to which the shortcut belongs.    |
| bundleName              | string                                     | Yes  | No  | Name of the bundle that contains the shortcut.        |
| hostAbility             | string                                     | Yes  | No  | Local ability information of the shortcut.   |
| icon                    | string                                     | Yes  | No  | Icon of the shortcut.              |
| iconId<sup>8+</sup>     | number                                     | Yes  | No  | Icon ID of the shortcut.            |
| label                   | string                                     | Yes  | No  | Label of the shortcut.              |
| labelId<sup>8+</sup>    | number                                     | Yes  | No  | Label ID of the shortcut.            |
| disableMessage          | string                                     | Yes  | No  | Message displayed when the shortcut is disabled.          |
| wants                   | Array&lt;[ShortcutWant](#shortcutwant)&gt; | Yes  | No  | Want information required for the shortcut.        |
| isStatic                | boolean                                    | Yes  | No  | Whether the shortcut is static.          |
| isHomeShortcut          | boolean                                    | Yes  | No  | Whether the shortcut is a home shortcut.|
| isEnabled               | boolean                                    | Yes  | No  | Whether the shortcut is enabled.            |
| moduleName<sup>9+</sup> | string                                     | Yes  | No  | Module name of the shortcut.            |