---
title: "THREADPROPERTIES | Microsoft Docs"
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
  - "THREADPROPERTIES"
helpviewer_keywords: 
  - "THREADPROPERTIES 構造体"
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

スレッドのプロパティについて説明します。  
  
## 構文  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```c#  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## メンバー  
 dwFields  
 記述するこの構造体のフィールドに設定 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) の列挙体のフラグの組み合わせが有効です。  
  
 dwThreadId  
 スレッド ID  
  
 dwSuspendCount  
 スレッドの数を中断します。  
  
 dwThreadState  
 のスレッドのオペレーティング [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) の状態を示す列挙体の値。  
  
 bstrPriority  
 指定した文字スレッドの優先順位 ; たとえば「標準」重要な」normal 」または 「時間の先頭で。  
  
 bstName  
 スレッドの名前。  
  
 bstrLocation  
 通常実行が現在停止するメソッドの名前として表現されるスレッドの場所 \(通常は最上位のスタック フレーム\)。  
  
## 解説  
 この構造は [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) メソッドの呼び出しによって格納されます。  返される情報は\[出力\] ウィンドウ ENT0ENT の設定で使用されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)