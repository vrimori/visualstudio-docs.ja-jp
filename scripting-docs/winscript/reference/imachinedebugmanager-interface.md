---
title: "IMachineDebugManager インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManager インターフェイス"
ms.assetid: 0b7133bb-5a52-4036-b4db-d69260790db7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManager インターフェイス
コンピューターのデバッグ マネージャーへの主要なインターフェイス。  このインターフェイスは `IMachineDebugManagerCookie` のインターフェイスに似ています。  
  
 `IUnknown` から継承するメソッドに加え、`IMachineDebugManager` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)|実行中のアプリケーションのリストにアプリケーションが追加されます。|  
|[IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)|実行中のアプリケーションの一覧からアプリケーションを削除します。|  
|[IMachineDebugManager::EnumApplications](../../winscript/reference/imachinedebugmanager-enumapplications.md)|実行中のアプリケーションの現在のリストの列挙子を返します。|  
  
## 参照  
 [IMachineDebugManagerCookie インターフェイス](../../winscript/reference/imachinedebugmanagercookie-interface.md)