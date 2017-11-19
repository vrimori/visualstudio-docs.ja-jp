---
title: "IDebugFormatter::GetStringForVariant |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugFormatter.GetStringForVariant
apilocation: jscript.dll
helpviewer_keywords: IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfc31b0fdbf6d1f4a29b1322dc3a3c4015f9c8ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
指定されたバリアント値を表す文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pvar`  
 [in]文字列として表現するバリアント。  
  
 `nRadix`  
 [in]数値の値に対して使用する基数。  
  
 `pbstrValue`  
 [out]文字列を表す`pvar`です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、指定されたバリアント型の値を表す文字列を返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugFormatter インターフェイス](../../winscript/reference/idebugformatter-interface.md)