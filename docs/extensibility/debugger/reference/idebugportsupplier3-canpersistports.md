---
title: "IDebugPortSupplier3::CanPersistPorts |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords: IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95e62f283d2ea0411162fb0406c712f0d17a1183
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
このメソッドは、ポート サプライヤーが、(それらをディスクに書き込む) をポートをデバッガーの呼び出しの間で永続化できるかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`ポートは、永続化できる場合、または`S_FALSE`ポートを永続化できないことを示すためにします。  
  
## <a name="remarks"></a>コメント  
 ポート サプライヤー ポートが永続できる場合が破棄されるときにそのし、次にもう一度がインスタンスに再読み込みします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)