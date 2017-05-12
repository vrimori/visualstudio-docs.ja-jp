---
title: "IMachineDebugManagerEvents インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerEvents インターフェイス"
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerEvents インターフェイス
コンピューターで保持される実行中のアプリケーションのリストの変更通知のは、マネージャーをデバッグします。  デバッガーの IDE でこのインターフェイスはアプリケーションの動的な一覧を表示するために使用できます。  
  
 `IUnknown` から継承するメソッドに加え、`IMachineDebugManagerEvents` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|アプリケーションが実行中のアプリケーションのリストに追加されたときにイベントを処理します。|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|アプリケーションが実行中のアプリケーションのリストから削除されたときにイベントを処理します。|