---
title: IDebugAddress2::GetProcessID |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fbe84371deb7306300c69f4890398fd43c3061f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099539"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
これによって表されるオブジェクトを所有するプロセスの ID を取得[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)インターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```csharp  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pProcID`  
 [out]プロセス id です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)