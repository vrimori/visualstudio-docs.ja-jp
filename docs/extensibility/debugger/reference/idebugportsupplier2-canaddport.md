---
title: "IDebugPortSupplier2::CanAddPort |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier2::CanAddPort
helpviewer_keywords: IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6f19d220f8638b84e194ab1604816ed767d10c41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
ポートのサプライヤーに新しいポートを追加することを確認します。  
  
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
 ポートを追加できる場合を返します`S_OK`、それ以外を返します`S_FALSE`をこのポートの仕入先のポートを追加することを示します。  
  
## <a name="remarks"></a>コメント  
 このメソッドを呼び出す前に、 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)ポートだけでなく、時間のかかる操作を追加するには、後者のメソッドが作成するためのメソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)