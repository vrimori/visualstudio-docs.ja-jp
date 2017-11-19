---
title: "IActiveScriptSite::OnLeaveScript |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
スクリプト コードを実行してから、スクリプト エンジンが返されたことをホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は `S_OK` を返します。  
  
## <a name="remarks"></a>コメント  
 スクリプト エンジンでは、スクリプト エンジンが入力された呼び出し元のアプリケーションに制御を返す前に、このメソッドを呼び出す必要があります。 たとえば、スクリプト オブジェクトを呼び出すスクリプト エンジンによって処理されるイベントを発生させる場合は、スクリプト エンジンで、呼び出す必要があります、 [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)メソッド、イベントを実行する前にを呼び出す必要がありますと`IActiveScriptSite::OnLeaveScript`イベントを発生させたオブジェクトを返す前に、イベントを実行した後です。 このメソッドの呼び出しを入れ子にすることができます。 すべての呼び出しに`IActiveScriptSite::OnEnterScript`このメソッドに対応する呼び出しが必要です。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)