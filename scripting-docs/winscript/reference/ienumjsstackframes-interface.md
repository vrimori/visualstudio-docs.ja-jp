---
title: "IEnumJsStackFrames インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12583f73c9f3977371ebd193716f2513fc0befc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames インターフェイス
JavaScript の jscript9diag.dll でスタック アンワインドが可能になるようにデバッガーによって実装されます。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next メソッド](../../winscript/reference/ienumjsstackframes-next-method.md)|指定した数のフレームを取得します。|  
|[IEnumJsStackFrames::Reset メソッド](../../winscript/reference/ienumjsstackframes-reset-method.md)|スタック フレームを最初の要素の前の位置にリセットします。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)