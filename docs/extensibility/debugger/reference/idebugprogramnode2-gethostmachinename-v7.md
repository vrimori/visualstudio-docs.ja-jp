---
title: "IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetHostMachineName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetHostMachineName_V7"
  - "IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName"
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramNode2::GetHostMachineName_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

使用されていません。  使用しないでください。  
  
## 構文  
  
```cpp#  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```c#  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### パラメーター  
 `pbstrHostMachineName`  
 \[入力\] プログラムを実行するコンピューターの名前を返します。  
  
## 戻り値  
 実装は `E_NOTIMPL` を常に返す必要です。  
  
## 解説  
  
> [!WARNING]
>  [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] 時点ではこのメソッドは使用されなくなり`E_NOTIMPL` を常に返す必要です。  
  
## 参照  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)