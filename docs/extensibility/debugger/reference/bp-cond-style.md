---
title: "BP_COND_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_COND_STYLE"
helpviewer_keywords: 
  - "BP_COND_STYLE 列挙型"
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

保留中およびバインド ブレークポイントの場合ブレークポイント条件のスタイルを指定します。  
  
## 構文  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```c#  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## メンバー  
 BP\_COND\_NONE  
 ブレークポイントの位置に到達するとブレークポイントを発生させます。  指定されたブレークポイント条件がありません。  
  
 BP\_COND\_WHEN\_TRUE  
 ブレークポイントに関連付けられた条件式が `true` の場合にだけブレークポイントを発生させます。  
  
 BP\_COND\_WHEN\_CHANGED  
 ブレークポイントに関連付けられた前の評価から条件式の値が変更された場合のみブレークポイントを発生させます。  
  
## 解説  
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) の構造体のメンバー `styleCondition` に使用されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)