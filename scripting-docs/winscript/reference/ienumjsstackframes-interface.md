---
title: IEnumJsStackFrames インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c26470e02f6c7e5d8911df7e743bce0cb0e560bb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087881"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames インターフェイス
JavaScript の jscript9diag.dll でスタック アンワインドが可能になるようにデバッガーによって実装されます。  
  
## <a name="syntax"></a>構文  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="public-methods"></a>パブリック メソッド  
  
|名前|説明|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next メソッド](../../winscript/reference/ienumjsstackframes-next-method.md)|指定した数のフレームを取得します。|  
|[IEnumJsStackFrames::Reset メソッド](../../winscript/reference/ienumjsstackframes-reset-method.md)|スタック フレームを最初の要素の前の位置にリセットします。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)