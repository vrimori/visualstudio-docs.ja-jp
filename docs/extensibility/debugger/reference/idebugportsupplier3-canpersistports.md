---
title: "IDebugPortSupplier3::CanPersistPorts |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7cb364ca40c42a3f392a5944169b7dd97075ab9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)