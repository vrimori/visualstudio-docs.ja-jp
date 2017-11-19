---
title: "IDebugAddress2::GetProcessID |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress2::GetProcessID
helpviewer_keywords: IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35ed788f5ac49b92b8702d433aa46df7571267d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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