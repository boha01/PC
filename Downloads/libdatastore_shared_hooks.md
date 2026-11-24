# قائمة الهوكات (Hooks) في `libdatastore_shared.so`

مرجع شامل لجميع دوال الهوك المستخرجة من مكتبة `libdatastore_shared.so` (`DobbyHook` و`SrSafeHook` عند `0x62fa8`)، مقسّمة حسب الوظيفة مع أسماء المساحات والصفوف والدوال والمواضع داخل قسم `.text`.

---

## القسم 1: تزوير معرّف الجهاز وفك الحظر (`SR-SPOOF`)
تستدعي `DobbyHook@PLT` مباشرةً لتعديل معرّف الجهاز المرسل عند تسجيل الدخول/التحقق:

| المساحة والصف (Namespace & Class) | الدالة (Method) | موضع الاستدعاء |
| :--- | :--- | :--- |
| `UnityEngine.SystemInfo` | `get_deviceUniqueIdentifier` | `0x0bdae0` |
| `dev.Scripts.GameScripts.Authorization.SpecificWindows.AuthorizationMetaModel` | `FromDevice` | `0x0bdc34` |
| `dev.Scripts.GameScripts.Authorization.SpecificWindows.AuthorizationMetaModel` | `FillSelfExtended` | `0x0bdcac` |
| `dev.Scripts.ECS.Morpeh.Features.SettingsFeature.Systems.SettingsServiceSystem` | `GetDeviceId` | `0x0bdd5c` |

---

## القسم 2: الـ ESP وتتبع المواقع والفيزياء (`ESP` & `Physics`)

| المساحة والصف (Namespace & Class) | الدالة (Method) | الوسم الداخلي | موضع الاستدعاء |
| :--- | :--- | :--- | :--- |
| `UnityEngine.Transform` | `set_position` | `Transform.set_position` | `0x066cc0` |
| `UnityEngine.Transform` | `set_localPosition` | `Transform.set_localPosition` | `0x066d34` |
| `UnityEngine.Transform` | `SetPositionAndRotation` | `Transform.SetPositionAndRotation` | `0x066da8` |
| `Lightbug.CharacterControllerPro.Core.PhysicsActor` | `Update` | `PhysicsActor.Update` | `0x072260` |
| `Lightbug.CharacterControllerPro.Core.PhysicsActorSync` | `FixedUpdate` | `PhysicsActorSync.FixedUpdate` | `0x0722c4` |

---

## القسم 3: التصويب الصامت واختراق الجدران (`SilentAim` & `WallPen`)

| المساحة والصف (Namespace & Class) | الدالة (Method) | الوسم الداخلي | موضع الاستدعاء |
| :--- | :--- | :--- | :--- |
| `dev.Scripts.ECS.Morpeh.Features.WeaponFeature.Systems.WeaponProduceAttackRangedSystem` | `RayCastAttackRanged` (7 معاملات) | `RayCastAttackRanged.7` | `0x0690a0` |
| `dev.Scripts.ECS.Morpeh.Features.WeaponFeature.Systems.WeaponProduceAttackRangedSystem` | `RayCastAttackRanged` (8 معاملات) | `RayCastAttackRanged.8` | `0x0690e0` |
| `dev.Scripts.ECS.Morpeh.Features.WeaponFeature.Systems.WeaponProduceAttackRangedSystem` | `OnUpdate` | `WeaponSystem.OnUpdate` | `0x069120` |
| `dev.Scripts.ECS.Morpeh.Features.WeaponFeature.Systems.WeaponProduceAttackRangedSystem` | `ProcessHits` (6 معاملات) | `ProcessHits` | `0x069160` |
| `dev.Scripts.ECS.Morpeh.Features.WeaponFeature.Systems.WeaponProduceAttackRangedSystem` | `GetPenetrationParameters` | `WallPen.GetPenParams` | `0x05b330` |
| `dev.Scripts.ECS.Morpeh.Features.WeaponFeature.Systems.WeaponProduceAttackRangedSystem` | `TryGetPenetrationDistance` | `WallPen.TryGetPenDist` | `0x05b39c` |

---

## القسم 4: الكاميرا والمنظور والمشاهدة (`FOV` / `FreeCam` / `Spectate`)

| المساحة والصف (Namespace & Class) | الدالة (Method) | الوسم الداخلي | موضع الاستدعاء |
| :--- | :--- | :--- | :--- |
| `UnityEngine.Camera` | `set_fieldOfView` | `Camera.set_fieldOfView` | `0x0674f4` |
| `UnityEngine.Camera` | `get_fieldOfView` | `Camera.get_fieldOfView` | `0x067530` |
| `dev.Scripts.ECS.Morpeh.Features.MainCameraFeature.Systems.Universal.UniversalCameraSystem` | `ApplyInputWithVerticalRotationLimit` | — | `0x06b7b0` |
| `dev.Scripts.ECS.Morpeh.Features.MainCameraFeature.Systems.CameraFollowingPedSystem` | `OnUpdate` | `FreeCam` | `0x07c0e4` (حلقة) |
| `dev.Scripts.ECS.Morpeh.Features.MainCameraFeature.Systems.CameraFollowingVehicleSystem` | `OnUpdate` | `FreeCam` | `0x07c0e4` (حلقة) |
| `dev.Scripts.ECS.Morpeh.Features.MainCameraFeature.Systems.CameraPlacementSystem` | `OnUpdate` | `FreeCam` | `0x07c0e4` (حلقة) |
| `dev.Scripts.ECS.Morpeh.Features.SoundFmodFeature.Services.SoundFmodPriorityService` | `SwitchListener` | `SoundFmod.SwitchListener` | `0x0bd4e0` |

---

## القسم 5: الطيران في السماء والجود مود وتكبير الرأس (`SkyWalk` / `GodMode` / `Head`)

| المساحة والصف (Namespace & Class) | الدالة (Method) | الوسم الداخلي | موضع الاستدعاء |
| :--- | :--- | :--- | :--- |
| `Lightbug.CharacterControllerPro.Core.CharacterActor` | `Update` | `SkyWalk.Update` | `0x073184` |
| `Lightbug.CharacterControllerPro.Core.CharacterActor` | `PostSimulationUpdate` | `SkyWalk.PostSim` | `0x0731dc` |
| `Lightbug.CharacterControllerPro.Core.CharacterActor` | `PreSimulationUpdate` | `SkyWalk.PreSim` | `0x073234` |
| `Lightbug.CharacterControllerPro.Core.CharacterActor` | `get_IsStable` | `SkyWalk.IsStable` | `0x07328c` |
| `Lightbug.CharacterControllerPro.Core.CharacterActor` | `get_IsGrounded` | `SkyWalk.ActorIsGrounded` | `0x0732e4` |
| `Lightbug.CharacterControllerPro.Core.CharacterActor` | `ForceNotGrounded` | `SkyWalk.ForceNotGrounded` | `0x07333c` |
| `Lightbug.CharacterControllerPro.Core.CharacterActor` | `LateUpdate` | `CharActor.LateUpdate(head)` | `0x073998` |
| `dev.Scripts.ECS.Morpeh.Features.PedViewFeature.DataContainers.PedKnockoutParameters` | `GetFallDamage` / `CalculateFallDamage` | `SkyWalk.FallDamage` | `0x0733fc` |
| `dev.Scripts.ECS.Morpeh.Features.PedViewFeature.StateMachine.States.Fall.FallState` | `CanEnterState` | `SkyWalk.FallState` | `0x073488` |
| `dev.Scripts.ECS.Morpeh.Features.PedViewFeature.StateMachine.PedStateMachine` | `ForceExit` | `SkyWalk.ForceExit` | `0x073514` |
| `dev.Scripts.ECS.Morpeh.Features.PedViewFeature.StateMachine.PedStateMachine` | `TryEnter` | `SkyWalk.TryEnter` | `0x073568` |
| `dev.Scripts.ECS.Morpeh.Features.PedViewFeature.StateMachine.PedStateMachine` | `ForceEnter` | `GodMode.ForceEnter` | `0x07366c` |
| `dev.Scripts.ECS.Morpeh.Features.PedViewFeature.StateMachine.States.Weapon.WeaponRangeShootState` | `CanEnterState` | `SkyWalk.WeaponShoot` | `0x0736f8` |
| `dev.Scripts.ECS.Morpeh.Features.PedViewFeature.StateMachine.PedState` | `CanEnterState` | `SkyWalk.PedState` | `0x0737d0` |

---

## القسم 6: الصحة وضرر السقوط ومؤشرات الواجهة (`Health` / `FallDamage` / `Slider`)

| المساحة والصف (Namespace & Class) | الدالة (Method) | الوسم الداخلي | موضع الاستدعاء |
| :--- | :--- | :--- | :--- |
| `ElementHealthSyncSystem` | `OnUpdate` | `ElementHealthSync.OnUpdate` | `0x05e638` |
| `UpdateHudHealthViewSystem` | `OnUpdate` | `HudHealthView.OnUpdate` | `0x05e67c` |
| `UnityEngine.UI.Slider` | `set_value` | `Slider.set_value` | `0x05eb64` |
| `UnityEngine.UI.Slider` | `SetValueWithoutNotify` | `Slider.SetSilent` | `0x05eb94` |
| `PedViewKnockoutService` | `ApplyLocalFallDamage` | `FallDamage.Apply` | `0x05ebd8` |

---

## القسم 7: السرعة، المشي في الهواء، المشي التلقائي، والخريطة (`Speed` / `WalkOnAir` / `AutoWalk` / `Pull`)

| المساحة والصف (Namespace & Class) | الدالة (Method) | الوسم الداخلي | موضع الاستدعاء |
| :--- | :--- | :--- | :--- |
| `Lightbug.CharacterControllerPro.Core.PhysicsActor` | `get_Velocity` | `PhysicsActor.get_Velocity` | `0x0757f4` |
| `Lightbug.CharacterControllerPro.Core.PhysicsActor` | `FixedUpdate` | `PhysicsActor.FixedUpdate` | `0x07bdc4` |
| `Lightbug.CharacterControllerPro.Core.PhysicsActor` | `Update` | `PhysicsActor.Update(woa)` | `0x07be78` |
| `dev.Scripts.ECS.Morpeh.Features.PedViewFeature.Systems.PedViewInputsSystem` | `update` | `PedViewInputsSystem.update` | `0x062e04` |
| `dev.Scripts.Map.NavigationGraph` | `FindPath` | `NavGraph.FindPath` | `0x07983c` |
| `dev.Scripts.Map.NavigationGraph` | `.ctor` | `NavGraph.ctor` | `0x0798e0` |
| `dev.Scripts.Map.NavigationGraph` | `SetGoal` | `NavGraph.SetGoal` | `0x07999c` |
| `dev.Scripts.Map.NavigationGraph` | `SetWaypoint` | `NavGraph.SetWaypoint` | `0x079a08` |
| `dev.Scripts.Map.NavigationGraph` | `SetDestination` | `NavGraph.SetDestination` | `0x079a74` |
| `dev.Scripts.Map.NavigationGraph` | `AddMarker` | `NavGraph.AddMarker` | `0x079ae0` |

---

## القسم 8: مزامنة الملابس والمركبات والستامينا (`CLSV-HOOKS` & `CarFeatures`)

| المساحة والصف (Namespace & Class) | الدالة (Method) | الوسم الداخلي | موضع الاستدعاء |
| :--- | :--- | :--- | :--- |
| `dev.Scripts.ECS.Morpeh.Features.PedsFeature.Systems.Streaming.PedLoadClothesSystem` | `OnUpdate` | `PedLoadClothes.OnUpdate` | `0x098cec` |
| `dev.Scripts.ECS.Systems.ProxySystems.GeneralElementInterpolateTransformSystem` | `OnUpdate` | `Interp.OnUpdate` | `0x098f38` |
| `dev.Scripts.ECS.Morpeh.Features.VehicleViewFeature.Systems.VehicleBody.VehicleBodyPrePhysicsSystem` | `OnUpdate` | `VehBody.OnUpdate` | `0x099058` |
| `PedChangeClothesSyncSystem` | `OnUpdate` | `PedClothesSync.OnUpdate` | `0x0990d0` |
| `ElementModelSyncSystem` | `OnUpdate` | `ElementModelSync.OnUpdate` | `0x0991e8` |
| `dev.Scripts.ECS.Morpeh.Features.PedViewFeature.Systems.PedViewStorage` | `SetStaminaLose` | `CarFeatures.SetStaminaLose` | `0x0bd6f4` |
| `dev.Scripts.ECS.Morpeh.Features.PedsFeature.Systems.PedValues.PedStaminaSystem` | `OnUpdate` | `CarFeatures.PedStamina` | `0x0bd83c` |

---

## القسم 9: الإضاءة ومدى الرؤية (`DAYNIGHT` & `SR-RANGE`)

| المساحة والصف (Namespace & Class) | الدالة (Method) | الوسم الداخلي | موضع الاستدعاء |
| :--- | :--- | :--- | :--- |
| `SkyLightingDriver` | `LateUpdate` | `SkyDriver.LateUpdate` | `0x05a358` |
| `RemoteCollisionCullingSystem` | `OnUpdate` | `SR-RANGE` | `0x0c008c` (حلقة) |
| `RemoteCollisionCullingRestoreSystem` | `OnUpdate` | `SR-RANGE` | `0x0c008c` (حلقة) |
| `PedViewInVehicleVisibilityDistanceSystem` | `OnUpdate` | `SR-RANGE` | `0x0c008c` (حلقة) |
| `PedViewVisibilityUpdateSystem` | `OnUpdate` | `SR-RANGE` | `0x0c008c` (حلقة) |
| `VehiclesDistanceCheckSystem` | `OnUpdate` | `SR-RANGE` | `0x0c008c` (حلقة) |

---

## القسم 10: دوال التغليف والبنية التحتية للهوك (`Internal Plumbing`)
- **`SrSafeHook` (`0x062fa8`)**: الدالة الوسيطة المسؤولة عن تغليف استدعاء `DobbyHook@PLT` (`0x063338`) مع التحقق الآمن وتسجيل النجاح/الفشل (`SR-SAFE: hooked` / `SR-SAFE: DobbyHook FAILED`).
- **`CodePatch@PLT` (`0x103c80`)**: لتعديل بايتات التعليمات مباشرة في الذاكرة عبر `mprotect`.
