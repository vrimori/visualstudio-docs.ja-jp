---
title: "IActiveScriptSite::OnEnterScript |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb4514770faaaad46c8590e6df03488e3d5bc679
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
スクリプト エンジンのスクリプト コードの実行が開始したことをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は `S_OK` を返します。  
  
## <a name="remarks"></a>コメント  
 スクリプト エンジンは、スクリプト エンジンに、エントリまたは再入するたびにこのメソッドを呼び出す必要があります。 たとえば、スクリプト オブジェクトを呼び出すスクリプト エンジンによって処理されるイベントを発生させる場合は、スクリプト エンジンで、呼び出す必要があります`IActiveScriptSite::OnEnterScript`前に、イベントを実行して、呼び出す必要があります、 [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)メソッド、イベントを実行した後は、イベントを発生させたオブジェクトを返す前にします。 このメソッドの呼び出しを入れ子にすることができます。 このメソッドを呼び出すたびに対応する呼び出しを要求する`IActiveScriptSite::OnLeaveScript`です。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)