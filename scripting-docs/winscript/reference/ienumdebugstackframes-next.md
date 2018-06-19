---
title: IEnumDebugStackFrames::Next |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e148b5e13bc3d7986451ece11a3a2eada5baa28
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728462"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
指定した列挙のシーケンス内のセグメント数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]取得するセグメントの数。  
  
 `prgdsfd`  
 [out]配列を返します`DebugStackFrameDescriptor`を取得してセグメントを表すインターフェイス。  
  
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
 [IEnumDebugStackFrames インターフェイス](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [DebugStackFrameDescriptor 構造体](../../winscript/reference/debugstackframedescriptor-structure.md)