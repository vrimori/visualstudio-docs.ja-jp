---
title: "MACHINE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MACHINE_INFO"
helpviewer_keywords: 
  - "MACHINE_INFO 構造体"
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# MACHINE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

特定のコンピューターについて説明します。  
  
## 構文  
  
```cpp#  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```c#  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## メンバー  
 `Fields`  
 構造体のフィールドが初期化を指定する [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) の列挙体のフラグの組み合わせ。  
  
 `bstrName`  
 コンピューター名。  [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md) を呼び出すことと同じです。  
  
 `Flags`  
 コンピューターの属性を記述する [MACHINE\_INFO\_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) の列挙体のフラグの組み合わせ。  
  
## 解説  
 この構造は [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md) メソッドの呼び出しによって返されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)