---
title: IDebugPortSupplier3::CanPersistPorts |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d9038663bd74b5dabeda92d8b6b9e4e31d092de
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939967"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
このメソッドは、ポート サプライヤーが、(ディスクに書き込む) ことによってポートをデバッガーの呼び出しの間で永続化できるかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` ポートは、永続化する場合または`S_FALSE`をポートを保存できないことを示します。  
  
## <a name="remarks"></a>Remarks  
 ポート サプライヤーがポートを永続化できる場合が破棄されるようにする必要があり、もう一度インスタンス化されるときに再読み込みします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)