# GAS

## 3.5 GAS in Multiplayer

Replication：单向，从服务器到客户端，因此Replicated actor不能在客户端修改。

RPC：remote procedure calls，从客户端发送到服务器

## 3.7 ReplicationMode

Minimal, Mixed, Full

## 3.8 Init Ability Actor Info

包含两个Actor: OwnerActor(PlayerState)和AvatarActor(PlayerCharacter)

对于Mixed，OwnerActor必须是Controller. （Set Owner）

## 4.1 Attributes

Gameplay Effect来修改Attribute，可以让客户端先生效，然后服务端撤销。GAS内置预测功能，不用额外考虑延迟补偿。

## 4.2 Health and Mana

在GAS中新建一个需要Repliacted的属性：创建`UPROPERTY(ReplicatedUsing=OnRep_xxx)`，这样会在复制时调用OnRep_xxx函数。创建`UFUNCTION() OnRep_xxx(FGameplayAttributeData& Oldxxx) const;`最后在函数中调用`GAMEPLAYATTRIBUTE_REPNOTIFY(UAuraAttributeSet, Health, OldHealth)`。并且在重写的`GetLifetimeReplicatedProps(TArray<FLifetimeProperty>& OutLifetimeProps) const`中注册`DOREPLIFETIME_CONDITION_NOTIFY(UAuraAttributeSet, Health, COND_None, REPNOTIFY_Always);`

## 4.3 Attribute Accessors

属性包含base value（白值）和current value（buff后的生效值）。