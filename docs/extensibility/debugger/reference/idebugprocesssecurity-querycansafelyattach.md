---
title: IDebugProcessSecurity::QueryCanSafelyAttach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9ecc1d7970fe8be98d199130db6e87847de3aee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839006"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
このメソッドは、ユーザーが安全でないプロセスにアタッチする前に警告を表示するポートのサプライヤーを使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>戻り値  
 戻り値は次のとおりです。  
  
-   `S_OK`:安全ではプロセスにアタッチして、警告ダイアログ ボックスは表示されません。  
  
-   `S_FALSE`:アタッチは、セキュリティ問題と、警告ダイアログ ボックスが表示されます。  
  
-   `FAILURE`:プロセスへのアタッチに失敗します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)