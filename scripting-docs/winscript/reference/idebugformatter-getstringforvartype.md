---
title: IDebugFormatter::GetStringForVarType |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVarType
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVarType
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06c4833e2d9a88b63a80b2ee9437dc5547579380
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087544"
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
指定した VARTYPE 値を表す文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `vt`  
 [in]文字列として表す VARTYPE します。  
  
 `ptdescArrayType`  
 [in]型を記述する構造体の配列。  
  
 `pbstr`  
 [out]文字列を表す`vt`します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 メソッドは、指定した VARTYPE 値を表す文字列を返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugFormatter インターフェイス](../../winscript/reference/idebugformatter-interface.md)