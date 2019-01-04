---
title: IDebugProgram2::Detach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Detach
helpviewer_keywords:
- IDebugProgram2::Detach
ms.assetid: 5e8d88b0-a8d4-4746-88c0-ad332ee73f33
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 44ad03f53e6bc8e96f762d83a0b0968ecb028184
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880235"
---
# <a name="idebugprogram2detach"></a>IDebugProgram2::Detach
プログラムのデバッグ エンジンをデタッチします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 デタッチされたプログラムの実行が継続しますが、デバッグ セッションの一部ではなくなりました。 デバッグ エンジンをデタッチしたら、これ以上のプログラムのデバッグ イベントが送信されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)