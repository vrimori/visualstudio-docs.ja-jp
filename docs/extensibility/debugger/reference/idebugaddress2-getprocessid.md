---
title: "IDebugAddress2::GetProcessID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress2::GetProcessID"
helpviewer_keywords: 
  - "IDebugAddress2::GetProcessID メソッド"
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugAddress2::GetProcessID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)このインターフェイスで表されるオブジェクトを所有するプロセスの ID を取得します。  
  
## 構文  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```c#  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### パラメーター  
 `pProcID`  
 \[プロセス ID\]  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)