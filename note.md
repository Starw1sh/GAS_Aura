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