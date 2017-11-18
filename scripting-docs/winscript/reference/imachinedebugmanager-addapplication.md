---
title: "IMachineDebugManager::AddApplication |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManager.AddApplication
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77c31084ccc24a6bace18f009eb8372a4f68a428
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
実行にアプリケーションを追加するアプリケーションの一覧です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pda`  
 [in]アプリケーションの実行中にアプリケーションの一覧です。  
  
 `pdwAppCookie`  
 [out]アプリケーションをマシン デバッグ マネージャーから削除するために使用する cookie です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、プロセスのデバッグ マネージャーされるたびに`IProcessDebugManager::AddApplication`と呼びます。  
  
## <a name="see-also"></a>関連項目  
 [IMachineDebugManager インターフェイス](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)