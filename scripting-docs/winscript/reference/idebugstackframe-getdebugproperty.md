---
title: IDebugStackFrame::GetDebugProperty |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDebugProperty
ms.assetid: e03c7504-bce4-4a44-81e4-db8c0216538d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 898c80dc4f5ef9010db6396a78c1b17b50603dc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726892"
---
# <a name="idebugstackframegetdebugproperty"></a>IDebugStackFrame::GetDebugProperty
現在のフレームのプロパティ ブラウザーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDebugProperty(  
   IDebugProperty**  ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppDebugProp`  
 [out]現在のフレームのプロパティ ブラウザー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、現在のフレームのプロパティ ブラウザーを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugStackFrame インターフェイス](../../winscript/reference/idebugstackframe-interface.md)