---
title: StackFrameTypeEnum |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb233000eb9bc0684858a82bf63ac2d71dbd60e5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252268"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

スタック フレームの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 フレーム ポインターを指定します。FPO 情報を使用できます。  
  
 `FrameTypeTrap`  
 カーネル トラップ フレーム。  
  
 `FrameTypeTSS`  
 カーネル トラップ フレーム。  
  
 `FrameTypeStandard`  
 標準 EBP スタック フレーム。  
  
 `FrameTypeFrameData`  
 フレーム ポインターを指定します。フレーム データ情報は利用可能です。  
  
 `FrameTypeUnknown`  
 すべてのデバッグ情報がないフレーム。  
  
## <a name="remarks"></a>Remarks  
 この列挙体の値が呼び出しによって返される、 [idiastackframe::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)メソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)



