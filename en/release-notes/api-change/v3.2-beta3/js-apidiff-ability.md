# JS API Changes of the Ability Framework

The table below lists the APIs changes of the ability framework in OpenHarmony 3.2 Beta3 over OpenHarmony 3.2 Beta2.

## API Changes

| Module| Class| Method/Attribute/Enumeration/Constant| Change Type|
|---|---|---|---|
| abilityDelegator                          | AbilityDelegator          | waitAbilityStageMonitor(monitor: AbilityStageMonitor, callback: AsyncCallback\<AbilityStage>): void;<br>waitAbilityStageMonitor(monitor: AbilityStageMonitor, timeout: number, callback: AsyncCallback\<AbilityStage>): void;<br>waitAbilityStageMonitor(monitor: AbilityStageMonitor, timeout?: number): Promise\<AbilityStage>; | Added|
| abilityDelegator                          | AbilityDelegator          | removeAbilityStageMonitor(monitor: AbilityStageMonitor, callback: AsyncCallback\<void>): void;<br>removeAbilityStageMonitor(monitor: AbilityStageMonitor): Promise\<void>;                                                                                                                                                    | Added|
| abilityDelegator                          | AbilityDelegator          | addAbilityStageMonitor(monitor: AbilityStageMonitor, callback: AsyncCallback\<void>): void;<br>addAbilityStageMonitor(monitor: AbilityStageMonitor): Promise\<void>;                                                                                                                                                          | Added|
| abilityStageMonitor                       | AbilityStageMonitor       | srcEntrance: string;                                                                                                                                                                                                                                                                                                           | Added|
| abilityStageMonitor                       | AbilityStageMonitor       | moduleName: string;                                                                                                                                                                                                                                                                                                            | Added|
| applicationInfo                           | ApplicationInfo           | readonly iconIndex: number;                                                                                                                                                                                                                                                                                                    | Added|
| applicationInfo                           | ApplicationInfo           | readonly labelIndex: number;                                                                                                                                                                                                                                                                                                   | Added|
| ApplicationStateObserver                  | ApplicationStateObserver  | onProcessStateChanged(processData: ProcessData): void;                                                                                                                                                                                                                                                                         | Added|
| context                                   | Context                   | getExternalCacheDir(callback: AsyncCallback\<string>): void<br>getExternalCacheDir(): Promise\<string>;                                                                                                                                                                                                                       | Added|
| lifecycle                                 | LifecycleForm             | onShare?(formId: string): {[key: string]: any};                                                                                                                                                                                                                                                                                | Added|
| MissionListener                           | MissionListener           | onMissionClosed(mission: number): void;                                                                                                                                                                                                                                                                                        | Added|
| ohos.ability.wantConstant                 | Action                    | DLP_PARAMS_INDEX = "ohos.dlp.params.index"                                                                                                                                                                                                                                                                                     | Added|
| ohos.ability.wantConstant                 | Action                    | DLP_PARAMS_ABILITY_NAME = "ohos.dlp.params.abilityName"                                                                                                                                                                                                                                                                        | Added|
| ohos.ability.wantConstant                 | Action                    | DLP_PARAMS_MODULE_NAME = "ohos.dlp.params.moduleName"                                                                                                                                                                                                                                                                          | Added|
| ohos.ability.wantConstant                 | Action                    | DLP_PARAMS_BUNDLE_NAME = "ohos.dlp.params.bundleName"                                                                                                                                                                                                                                                                          | Added|
| ohos.ability.wantConstant                 | Action                    | DLP_PARAMS_SANDBOX = "ohos.dlp.params.sandbox"                                                                                                                                                                                                                                                                                 | Added|
| ohos.ability.wantConstant                 | Action                    | ACTION_MARKET_CROWDTEST = "ohos.want.action.marketCrowdTest"                                                                                                                                                                                                                                                                   | Added|
| ohos.ability.wantConstant                 | Action                    | ACTION_MARKET_DOWNLOAD = "ohos.want.action.marketDownload"                                                                                                                                                                                                                                                                     | Added|
| ohos.abilityAccessCtrl                    | PermissionStateChangeInfo | permissionName: string;                                                                                                                                                                                                                                                                                                        | Added|
| ohos.abilityAccessCtrl                    | PermissionStateChangeInfo | tokenID: number;                                                                                                                                                                                                                                                                                                               | Added|
| ohos.abilityAccessCtrl                    | PermissionStateChangeInfo | change: PermissionStateChangeType;                                                                                                                                                                                                                                                                                             | Added|
| ohos.abilityAccessCtrl                    | PermissionStateChangeType | PERMISSION_GRANTED_OPER = 1                                                                                                                                                                                                                                                                                                    | Added|
| ohos.abilityAccessCtrl                    | PermissionStateChangeType | PERMISSION_REVOKED_OPER = 0                                                                                                                                                                                                                                                                                                    | Added|
| ohos.abilityAccessCtrl                    | AtManager                 | off(type: 'permissionStateChange', tokenIDList: Array\<number>, permissionNameList: Array\<string>, callback?: Callback\<PermissionStateChangeInfo>): void;                                                                                                                                                                    | Added|
| ohos.abilityAccessCtrl                    | AtManager                 | on(type: 'permissionStateChange', tokenIDList: Array\<number>, permissionNameList: Array\<string>, callback: Callback\<PermissionStateChangeInfo>): void;                                                                                                                                                                      | Added|
| ohos.abilityAccessCtrl                    | AtManager                 | getVersion(): Promise\<number>;                                                                                                                                                                                                                                                                                                | Added|
| ohos.application.Ability                  | Ability                   | onMemoryLevel(level: AbilityConstant.MemoryLevel): void;                                                                                                                                                                                                                                                                       | Added|
| ohos.application.AbilityConstant          | WindowMode                | WINDOW_MODE_FLOATING = 102                                                                                                                                                                                                                                                                                                     | Added|
| ohos.application.AbilityConstant          | WindowMode                | WINDOW_MODE_SPLIT_SECONDARY = 101                                                                                                                                                                                                                                                                                              | Added|
| ohos.application.AbilityConstant          | WindowMode                | WINDOW_MODE_SPLIT_PRIMARY = 100                                                                                                                                                                                                                                                                                                | Added|
| ohos.application.AbilityConstant          | WindowMode                | WINDOW_MODE_FULLSCREEN = 1                                                                                                                                                                                                                                                                                                     | Added|
| ohos.application.AbilityConstant          | WindowMode                | WINDOW_MODE_UNDEFINED = 0                                                                                                                                                                                                                                                                                                      | Added|
| ohos.application.AbilityConstant          | MemoryLevel               | MEMORY_LEVEL_CRITICAL = 2                                                                                                                                                                                                                                                                                                      | Added|
| ohos.application.AbilityConstant          | MemoryLevel               | MEMORY_LEVEL_LOW = 1                                                                                                                                                                                                                                                                                                           | Added|
| ohos.application.AbilityConstant          | MemoryLevel               | MEMORY_LEVEL_MODERATE = 0                                                                                                                                                                                                                                                                                                      | Added|
| ohos.application.AbilityLifecycleCallback | AbilityLifecycleCallback  | onWindowStageDestroy(ability: Ability, windowStage: window.WindowStage): void;                                                                                                                                                                                                                                                 | Added|
| ohos.application.AbilityLifecycleCallback | AbilityLifecycleCallback  | onWindowStageInactive(ability: Ability, windowStage: window.WindowStage): void;                                                                                                                                                                                                                                                | Added|
| ohos.application.AbilityLifecycleCallback | AbilityLifecycleCallback  | onWindowStageActive(ability: Ability, windowStage: window.WindowStage): void;                                                                                                                                                                                                                                                  | Added|
| ohos.application.AbilityLifecycleCallback | AbilityLifecycleCallback  | onWindowStageCreate(ability: Ability, windowStage: window.WindowStage): void;                                                                                                                                                                                                                                                  | Added|
| ohos.application.AbilityStage             | AbilityStage              | onMemoryLevel(level: AbilityConstant.MemoryLevel): void;                                                                                                                                                                                                                                                                       | Added|
| ohos.application.appManager               | ProcessState              | STATE_DESTROY                                                                                                                                                                                                                                                                                                                  | Added|
| ohos.application.appManager               | ProcessState              | STATE_BACKGROUND                                                                                                                                                                                                                                                                                                               | Added|
| ohos.application.appManager               | ProcessState              | STATE_ACTIVE                                                                                                                                                                                                                                                                                                                   | Added|
| ohos.application.appManager               | ProcessState              | STATE_FOREGROUND                                                                                                                                                                                                                                                                                                               | Added|
| ohos.application.appManager               | ProcessState              | STATE_CREATE                                                                                                                                                                                                                                                                                                                   | Added|
| ohos.application.appManager               | ApplicationState          | STATE_DESTROY                                                                                                                                                                                                                                                                                                                  | Added|
| ohos.application.appManager               | ApplicationState          | STATE_BACKGROUND                                                                                                                                                                                                                                                                                                               | Added|
| ohos.application.appManager               | ApplicationState          | STATE_ACTIVE                                                                                                                                                                                                                                                                                                                   | Added|
| ohos.application.appManager               | ApplicationState          | STATE_FOREGROUND                                                                                                                                                                                                                                                                                                               | Added|
| ohos.application.appManager               | ApplicationState          | STATE_CREATE                                                                                                                                                                                                                                                                                                                   | Added|
| ohos.application.Configuration            | Configuration             | hasPointerDevice?: boolean;                                                                                                                                                                                                                                                                                                    | Added|
| ohos.application.context                  | AreaMode                  | EL2 = 1                                                                                                                                                                                                                                                                                                                        | Added|
| ohos.application.context                  | AreaMode                  | EL1 = 0                                                                                                                                                                                                                                                                                                                        | Added|
| ohos.application.formError                | FormError                 | ERR_DISTRIBUTED_SCHEDULE_FAILED = 37                                                                                                                                                                                                                                                                                           | Added|
| ohos.application.FormExtension            | FormExtension             | onShare?(formId: string): {[key: string]: any};                                                                                                                                                                                                                                                                                | Added|
| ohos.application.formHost                 | formHost                  | function shareForm(formId: string, deviceId: string, callback: AsyncCallback\<void>): void;<br>function shareForm(formId: string, deviceId: string): Promise\<void>;                                                                                                                                                          | Added|
| ohos.application.formInfo                 | VisibilityType            | FORM_INVISIBLE: number                                                                                                                                                                                                                                                                                                         | Added|
| ohos.application.formInfo                 | VisibilityType            | FORM_VISIBLE: number,                                                                                                                                                                                                                                                                                                          | Added|
| ohos.application.formInfo                 | FormDimension             | Dimension_2_1                                                                                                                                                                                                                                                                                                                  | Added|
| ohos.application.formInfo                 | FormDimension             | Dimension_4_4                                                                                                                                                                                                                                                                                                                  | Added|
| ohos.application.formInfo                 | FormDimension             | Dimension_2_4                                                                                                                                                                                                                                                                                                                  | Added|
| ohos.application.formInfo                 | FormDimension             | Dimension_2_2                                                                                                                                                                                                                                                                                                                  | Added|
| ohos.application.formInfo                 | FormDimension             | Dimension_1_2 = 1                                                                                                                                                                                                                                                                                                              | Added|
| ohos.application.formInfo                 | FormParam                 | DEVICE_ID_KEY = "ohos.extra.param.key.device_id"                                                                                                                                                                                                                                                                               | Added|
| ohos.application.formInfo                 | FormParam                 | ABILITY_NAME_KEY = "ohos.extra.param.key.ability_name"                                                                                                                                                                                                                                                                         | Added|
| ohos.application.formInfo                 | FormParam                 | BUNDLE_NAME_KEY = "ohos.extra.param.key.bundle_name"                                                                                                                                                                                                                                                                           | Added|
| ohos.application.quickFixManager          | quickFixManager           | function getApplicationQuickFixInfo(bundleName: string, callback: AsyncCallback\<ApplicationQuickFixInfo>): void;<br>function getApplicationQuickFixInfo(bundleName: string): Promise\<ApplicationQuickFixInfo>;                                                                                                              | Added|
| ohos.application.quickFixManager          | quickFixManager           | function applyQuickFix(hapModuleQuickFixFiles: Array\<string>, callback: AsyncCallback\<void>): void;<br>function applyQuickFix(hapModuleQuickFixFiles: Array\<string>): Promise\<void>;                                                                                                                                      | Added|
| ohos.application.quickFixManager          | ApplicationQuickFixInfo   | readonly hapModuleQuickFixInfo: Array\<HapModuleQuickFixInfo>;                                                                                                                                                                                                                                                                 | Added|
| ohos.application.quickFixManager          | ApplicationQuickFixInfo   | readonly quickFixVersionName: string;                                                                                                                                                                                                                                                                                          | Added|
| ohos.application.quickFixManager          | ApplicationQuickFixInfo   | readonly quickFixVersionCode: number;                                                                                                                                                                                                                                                                                          | Added|
| ohos.application.quickFixManager          | ApplicationQuickFixInfo   | readonly bundleVersionName: string;                                                                                                                                                                                                                                                                                            | Added|
| ohos.application.quickFixManager          | ApplicationQuickFixInfo   | readonly bundleVersionCode: number;                                                                                                                                                                                                                                                                                            | Added|
| ohos.application.quickFixManager          | ApplicationQuickFixInfo   | readonly bundleName: string;                                                                                                                                                                                                                                                                                                   | Added|
| ohos.application.quickFixManager          | HapModuleQuickFixInfo     | readonly quickFixFilePath: string;                                                                                                                                                                                                                                                                                             | Added|
| ohos.application.quickFixManager          | HapModuleQuickFixInfo     | readonly originHapHash: string;                                                                                                                                                                                                                                                                                                | Added|
| ohos.application.quickFixManager          | HapModuleQuickFixInfo     | readonly moduleName: string;                                                                                                                                                                                                                                                                                                   | Added|
| ProcessData                               | ProcessData               | isKeepAlive: boolean;                                                                                                                                                                                                                                                                                                          | Added|
| ProcessData                               | ProcessData               | isContinuousTask: boolean;                                                                                                                                                                                                                                                                                                     | Added|
| ProcessData                               | ProcessData               | state: number;                                                                                                                                                                                                                                                                                                                 | Added|
| ServiceExtensionContext                   | ServiceExtensionContext   | startAbilityByCall(want: Want): Promise\<Caller>;                                                                                                                                                                                                                                                                              | Added|
| ohos.ability.wantConstant                  | Action                    | ACTION_MARKER_DOWNLOAD = "ohos.want.action.marketDownload"                                        | Deleted|
| ohos.application.AbilityLifecycleCallback  | AbilityLifecycleCallback  | onAbilityWindowStageDestroy(ability: Ability): void;                                              | Deleted|
| ohos.application.AbilityLifecycleCallback  | AbilityLifecycleCallback  | onAbilityWindowStageCreate(ability: Ability): void;                                               | Deleted|
| ohos.application.DataShareExtensionAbility | DataShareExtensionAbility | getType?(uri: string, callback: AsyncCallback\<string>): void;                                    | Deleted|
| ohos.application.DataShareExtensionAbility | DataShareExtensionAbility | openFile?(uri: string, mode: string, callback: AsyncCallback\<number>): void;                     | Deleted|
| ohos.application.DataShareExtensionAbility | DataShareExtensionAbility | getFileTypes?(uri: string, mimeTypeFilter: string, callback: AsyncCallback\<Array\<string>>): void; | Deleted|
| applicationInfo | ApplicationInfo | readonly iconId: string;           | Deprecated|
| applicationInfo | ApplicationInfo | readonly labelId: string;          | Deprecated|
| want            | Want            | entities?: Array\<string>;         | Deprecated|
| want            | Want            | parameters?: {[key: string]: any}; | Deprecated|
| want            | Want            | action?: string;                   | Deprecated|
| want            | Want            | flags?: number;                    | Deprecated|
| want            | Want            | type?: string;                     | Deprecated|
| want            | Want            | uri?: string;                      | Deprecated|
| want            | Want            | abilityName?: string;              | Deprecated|
| want            | Want            | bundleName?: string;               | Deprecated|
| want            | Want            | deviceId?: string;                 | Deprecated|