---
title: IVariantChangeType::ChangeType |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a02b8a3991ff6d20370cd4a2ea4cd87aa9a1226
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086581"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
バリアント型の値を受け取り、指定の型を持つ新しいバリアントを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pvarDst`  
 [入力、出力]によって表される値を格納するバリアント`pvarSrc`がで指定された型、`vtNew`します。  
  
 `pvarSrc`  
 [in]新しい種類を変更するのにはバリアント型の値。  
  
 `lcid`  
 [in]文字列と引数の変換時に使用するロケール コンテキスト。  
  
 `vtNew`  
 [in]型を指定します`pvarDst`になります。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 `pvarDst`と`pvarSrc`引数がありますと等しい場合は、この場合、元の値が上書きされます。 このメソッドは成功`pvarDst`を`VariantClear`関数の場合、その対策として`pvarDst`有効な値に初期化する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IVariantChangeType インターフェイス](../../winscript/reference/ivariantchangetype-interface.md)