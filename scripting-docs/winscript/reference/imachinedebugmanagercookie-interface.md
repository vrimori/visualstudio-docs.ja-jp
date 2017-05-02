---
title: "IMachineDebugManagerCookie インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IMachineDebugManagerCookie インターフェイス"
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie インターフェイス
`IMachineDebugManager` のインターフェイスと同様に、`IMachineDebugManagerCookie` のインターフェイスのサポートはクッキーをデバッグします。  
  
 このインターフェイスは、\( `IDebugCookie` のインターフェイスとともに\) スクリプトがデバッガーでは、これらのスクリプトを追跡することなく、スクリプト デバッガー プロセスで実行されます。  
  
 スクリプト デバッガーがデバッグ プロセスの Manager \(PDM\) `IDebugCookie::SetDebugCookie` のメソッドを呼び出します。  次に、PDM は `IMachineDebugManagerCookie` インターフェイスのメソッドを使用して、マシンのデバッグ マネージャーから、または \(MDM\) スクリプト アプリケーションを、追加、または削除する要求とともにこのクッキーを送信します。  MDM は、クッキーをいるものを除く、すべてのデバッガーの変更を、通知します。  
  
 `IUnknown` から継承するメソッドに加え、`IMachineDebugManagerCookie` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|実行中のアプリケーションのリストにアプリケーションが追加されます。|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|実行中のアプリケーションの現在のリストの列挙子を返します。|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|実行中のアプリケーションの一覧からアプリケーションを削除します。|  
  
## 参照  
 [IMachineDebugManager インターフェイス](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie インターフェイス](../../winscript/reference/idebugcookie-interface.md)