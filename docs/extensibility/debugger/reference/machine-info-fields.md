---
title: "MACHINE_INFO_FIELDS | Microsoft Docs"
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
  - "MACHINE_INFO_FIELDS"
helpviewer_keywords: 
  - "MACHINE_INFO_FIELDS 列挙型"
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

特定のコンピューターのために取得するような情報を指定します。  
  
## 構文  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## メンバー  
 MCIF\_NAME  
 構造体の初期化と `bstrName` のフィールドを使用します。  
  
 MCIF\_FLAGS  
 構造体の初期化と `Flags` のフィールドを使用します。  
  
 MIF\_ALL  
 すべての構造体フィールドの初期化とを使用します。  
  
## 解説  
 これらの値は [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md) のメソッドに [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md) の構造体のメンバーを初期化するかを示すために渡されます。  
  
 フィールドを使用して有効であることを示すために `MACHINE_INFO` の構造体の `Fields` のメンバーでも使用します。  
  
 これらのフラグはビットごと `OR` に組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)