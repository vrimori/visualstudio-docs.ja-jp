---
title: "IActiveScriptStats::GetStatEx |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb8adf27811f3046de7b447e537443ef129a8c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
カスタム スクリプトの統計情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `guid`  
 [in]返される統計情報を指定します。 セマンティクスの統計情報は、特定に対応する GUID 全体が定義されているエンジンです。  
  
 `pluHi`  
 [out]統計情報を表す 64 ビット符号なし整数の上位 32 ビットです。  
  
 `pluLo`  
 [out]統計情報を表す 64 ビット符号なし整数の下位 32 ビットです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|メソッドは実装されていません。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、カスタム ホストに意味のある統計情報を返すカスタム スクリプト エンジンを使用します。  
  
> [!NOTE]
>  このメソッドは現在実装されていません。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats インターフェイス](../../winscript/reference/iactivescriptstats-interface.md)