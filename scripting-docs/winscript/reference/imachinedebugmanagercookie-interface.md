---
title: "IMachineDebugManagerCookie インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie インターフェイス
ような`IMachineDebugManager`、インターフェイス、`IMachineDebugManagerCookie`インターフェイスは、デバッグの cookie をサポートしています。  
  
 このインターフェイス (と共に、`IDebugCookie`インターフェイス)、デバッガーでこれらのスクリプトの追跡を必要とせず、スクリプトのデバッガー プロセスで実行するスクリプトを許可します。  
  
 スクリプト デバッガーを呼び出して、`IDebugCookie::SetDebugCookie`メソッド プロセスをデバッグ マネージャー (PDM)。 次に、PDM 送信を追加または削除から、マシン デバッグ マネージャー (MDM)、またはスクリプト アプリケーションのすべての要求と共にこの cookie のメソッドを使用して、`IMachineDebugManagerCookie`インターフェイスです。 MDM をそのクッキーを持つものを除き、変更のすべてのデバッガー通知します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IMachineDebugManagerCookie`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|実行にアプリケーションを追加するアプリケーションの一覧です。|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|現在実行されているアプリケーションの一覧の列挙子を返します。|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|実行中からアプリケーションを削除するアプリケーションの一覧です。|  
  
## <a name="see-also"></a>関連項目  
 [IMachineDebugManager インターフェイス](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie インターフェイス](../../winscript/reference/idebugcookie-interface.md)