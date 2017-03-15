---
title: "IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::QueryCanSafelyAttach"
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはユーザーが危険なプロセスにアタッチする前にポートがサプライヤーの警告を表示できるようにします。  
  
## 構文  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```c#  
int QueryCanSafelyAttach();  
```  
  
## 戻り値  
 戻り値は次のとおりです。:  
  
-   `S_OK`: 処理対象のアタッチが安全であり警告ダイアログ ボックスは表示されません。  
  
-   `S_FALSE`: アタッチはセキュリティ上の問題にできますが警告ダイアログ ボックスが表示されます。  
  
-   `FAILURE`: アタッチするプロセスは失敗します。  
  
## 参照  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)