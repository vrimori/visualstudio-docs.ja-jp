---
title: IScriptEntry::SetBody |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06ee232aa730366e9a23e15cdc45f6734b9ef744
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729142"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
本文内にあるテキストを設定、`IScriptEntry`スクリプト ブロックまたは`IScriptScriptlet`スクリプトレットです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `psz`  
 [in]`IScriptEntry`スクリプト ブロック`psz`スクリプト タグで囲まれたテキストです。  
  
 `IScriptEntry`関数ブロック`psz`関数本文です。  
  
 `IScriptScriptlet`オブジェクト (から派生した`IScriptEntry`)、`psz`スクリプトレットのスクリプトのテキストです。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)