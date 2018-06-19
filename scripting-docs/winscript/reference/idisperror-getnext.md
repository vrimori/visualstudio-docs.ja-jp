---
title: IDispError::GetNext |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetNext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cbe4b044f2d3fb1d8ffb08565fc4093fbbe3ec7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728142"
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
次の取得`IDispError`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppde`  
 [out]次に示す`IDispError`オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、次を取得`IDispError`オブジェクト。 これは、最後の場合`IDispError`オブジェクトをこのメソッドに NULL が返されます。  
  
> [!NOTE]
>  このメソッドは実装されていません。  
  
## <a name="see-also"></a>関連項目  
 [IDispError インターフェイス](../../winscript/reference/idisperror-interface.md)