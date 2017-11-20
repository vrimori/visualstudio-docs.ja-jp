---
title: "IDebugExtendedField::IsClosedType |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad1498f0f169e10bcc58cdc0f5e041096766e87c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
フィールドがクローズ型を表すかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>戻り値  
 フィールドがクローズ型の場合を返します`S_OK`、それ以外を返します`S_FALSE`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)