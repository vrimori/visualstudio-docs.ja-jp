---
title: "BP_PASSCOUNT_STYLE | Microsoft Docs"
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
  - "BP_PASSCOUNT_STYLE"
helpviewer_keywords: 
  - "BP_PASSCOUNT_STYLE 構造体"
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ブレークポイントを発生させるブレークポイントのパスの数に関連付けられた条件を指定します。  
  
## 構文  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```c#  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## メンバー  
 BP\_PASSCOUNT\_NONE  
 ブレークポイントのパスの数のスタイルを指定しません。  
  
 BP\_PASSCOUNT\_EQUAL  
 等号とブレークポイントのパスの数のスタイルを設定します。  ブレークポイントのヒット回数があるパスの数がある場合ブレークポイントの起動します。  
  
 BP\_PASSCOUNT\_EQUAL\_OR\_GREATER  
 同じかそれよりも大きくブレークポイントのパスの数のスタイルを設定します。  回数がブレークポイントの場合ブレークポイントで起動するとヒット カウントが大きいパスの数。  
  
 BP\_PASSCOUNT\_MOD  
 残りのパスの数を指定します。  たとえばパスの数が型 `BP_PASSCOUNT_MOD` でパスの値が 4 の場合ヒット カウントが 4. の倍数するたびにブレークポイントを起動します。  
  
## 解説  
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)および [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) の構造体のメンバーである [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) の構造体のメンバー `stylePassCount` に使用されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)