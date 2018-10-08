---
title: IDebugAddress2::GetProcessID |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31c935db12a3cbac5bf4e85800e826e1972be4f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539649"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugAddress2::GetProcessID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugaddress2-getprocessid)します。  
  
これによって表されるオブジェクトを所有するプロセスの ID を取得[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)インターフェイス。  
  
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

