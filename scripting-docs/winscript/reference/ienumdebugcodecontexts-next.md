---
title: "IEnumDebugCodeContexts::Next |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugCodeContexts.Next
apilocation: jscript.dll
helpviewer_keywords: IEnumDebugCodeContexts::Next
ms.assetid: 844cc353-ae0b-45e1-84a6-32b0bb67f57f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00a3a5765f5b5a62753653d24cf27e4667a5647f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugcodecontextsnext"></a>IEnumDebugCodeContexts::Next
指定した列挙のシーケンス内のセグメント数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext**  pscc,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]取得するセグメントの数。  
  
 `pscc`  
 [out]配列を返します`IDebugCodeContext`を取得してセグメントを表すインターフェイス。  
  
 `pceltFetched`  
 [out]列挙子によってフェッチされたセグメントの実際の数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、指定した列挙のシーケンス内のセグメント数を取得します。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugCodeContexts インターフェイス](../../winscript/reference/ienumdebugcodecontexts-interface.md)