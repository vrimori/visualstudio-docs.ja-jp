---
title: IDebugProcessSecurity::QueryCanSafelyAttach |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 357ab447d0f16c3bbbfb656d042c0095df01bc83
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784443"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、ユーザーが安全でないプロセスにアタッチする前に警告を表示するポートのサプライヤーを使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>戻り値  
 戻り値は次のとおりです。  
  
-   `S_OK`。 安全ですプロセスにアタッチして、警告ダイアログ ボックスは表示されません。  
  
-   `S_FALSE`: セキュリティ問題になる可能性がありますアタッチし、警告ダイアログ ボックスが表示されます。  
  
-   `FAILURE`: 失敗プロセスにアタッチします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

