---
title: "IDebugProcessSecurity::QueryCanSafelyAttach |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5315281b904a6a4144f8e06780048e25cd5e0221
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
このメソッドは、警告を表示、ユーザーが安全でないプロセスにアタッチする前に、ポート業者を使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>戻り値  
 戻り値は次のとおりです。  
  
-   `S_OK`: プロセスにアタッチする安全では、警告ダイアログ ボックスは表示されません。  
  
-   `S_FALSE`: セキュリティ問題になる可能性がありますアタッチされ、警告ダイアログ ボックスが表示されます。  
  
-   `FAILURE`: プロセスへのアタッチに失敗します。  
  
## <a name="see-also"></a>参照  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)