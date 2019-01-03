---
title: IDebugPortSupplier2::CanAddPort |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18d728f762a9e4dd16930e4634c9cb0ca47b2bc8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853906"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
ポート サプライヤーが新しいポートを追加できることを確認します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>戻り値  
 ポートを追加できる場合を返します`S_OK`。 それ以外を返します`S_FALSE`を示すには、このポートのサプライヤーのポートは追加できません。  
  
## <a name="remarks"></a>Remarks  
 このメソッドを呼び出す前に、 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)メソッド後者の方法は、ポートに追加するには、時間のかかる操作になることがありますを作成するためです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)