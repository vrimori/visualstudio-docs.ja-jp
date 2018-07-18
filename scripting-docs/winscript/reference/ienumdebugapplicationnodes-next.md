---
title: IEnumDebugApplicationNodes::Next |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Next
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61bc2b677f12106c9bd8e6c8bec57ae1f7a09605
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727832"
---
# <a name="ienumdebugapplicationnodesnext"></a>IEnumDebugApplicationNodes::Next
指定した列挙のシーケンス内のセグメント数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]取得するセグメントの数。  
  
 `pprddp`  
 [out]配列を返します`IDebugApplicationNode`を取得してセグメントを表すインターフェイス。  
  
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
 [IEnumDebugApplicationNodes インターフェイス](../../winscript/reference/ienumdebugapplicationnodes-interface.md)