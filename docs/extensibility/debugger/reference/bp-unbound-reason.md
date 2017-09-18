---
title: "BP_UNBOUND_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_UNBOUND_REASON"
helpviewer_keywords: 
  - "BP_UNBOUND_REASON 列挙型"
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ブレークポイントが解放された理由を示します。  
  
## 構文  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```c#  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## メンバー  
 BPUR\_UNKNOWN  
 原因は不明です。  
  
 BPUR\_CODE\_UNLOADED  
 ブレークポイントが含まれるコードはアンロードを下されました。  
  
 BPUR\_BREAKPOINT\_REBIND  
 ブレークポイントは別の場所に反動です。  これはブレークポイントが移動したりブレークポイントは有効ではなくなるパスを使用してファイルにバインドされると編集後に発生することができる操作を継続します。  
  
 BPUR\_ BREAKPOINT\_ERROR  
 ブレークポイントはバインドした後間違うに決まります。  これは条件が有効ではなくマネージのブレークポイントに発生します。  
  
## 解説  
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) のメソッドによって返される。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)