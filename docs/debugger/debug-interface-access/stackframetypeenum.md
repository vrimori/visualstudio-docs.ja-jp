---
title: "StackFrameTypeEnum |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4dcb46fc2fb3936e0cee91426b4787945bd14f59
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>参照  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)