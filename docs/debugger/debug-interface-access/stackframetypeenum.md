---
title: StackFrameTypeEnum |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c791bbe28db35a33e433ce2e38fac2d34ba46f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
スタック フレームの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Elements  
 `FrameTypeFPO`  
 フレーム ポインターを指定します。FPO 情報は利用可能です。  
  
 `FrameTypeTrap`  
 カーネル トラップ フレームです。  
  
 `FrameTypeTSS`  
 カーネル トラップ フレームです。  
  
 `FrameTypeStandard`  
 標準的な EBP スタック フレーム。  
  
 `FrameTypeFrameData`  
 フレーム ポインターを指定します。フレーム データ情報は利用可能です。  
  
 `FrameTypeUnknown`  
 デバッグ情報がないフレームです。  
  
## <a name="remarks"></a>コメント  
 この列挙体の値がへの呼び出しによって返される、 [idiastackframe::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)