---
title: IVariantChangeType::ChangeType |Microsoft ドキュメント
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
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734202"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
バリアント型の値を取得し、種類を指定して新しいバリエーションを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pvarDst`  
 [入力、出力].によって表される値を格納するバリアント`pvarSrc`で指定された型で`vtNew`です。  
  
 `pvarSrc`  
 [in]新しい型に変更するバリアント型の値。  
  
 `lcid`  
 [in]文字列の間に、引数を変換するときに使用するロケール コンテキスト。  
  
 `vtNew`  
 [in]種類を示す`pvarDst`になります。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 `pvarDst`と`pvarSrc`引数がありますと等しい場合は、その場合、元の値が上書きされます。 このメソッドは成功`pvarDst`を`VariantClear`関数、およびその結果`pvarDst`有効な値に初期化する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IVariantChangeType インターフェイス](../../winscript/reference/ivariantchangetype-interface.md)