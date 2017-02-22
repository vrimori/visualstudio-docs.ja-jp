---
title: "メッセージの種類 | Microsoft Docs"
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
  - "MESSAGETYPE"
helpviewer_keywords: 
  - "MESSAGETYPE の列挙型"
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# メッセージの種類
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メッセージの種類と理由を指定します。  
  
## 構文  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```c#  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## メンバー  
 MT\_OUTPUTSTRING  
 メッセージが出力ウィンドウに送信する必要があることを示します。  これは `MT_MESSAGEBOX` から相互に排他的です。  
  
 MT\_MESSAGEBOX  
 メッセージをメッセージ ボックスに表示されることを示します。  これは `MT_OUTPUTSTRING` から相互に排他的です。  
  
 MT\_TYPE\_MASK  
 メッセージのコピー先を分離するマスクの値。  
  
 MT\_REASON\_EXCEPTION  
 メッセージ ボックスで例外の結果として表示されることを示します。  これは `MT_REASON_TRACEPOINT` から相互に排他的です。  
  
 MT\_REASON\_TRACEPOINT  
 メッセージ ボックスでトレース ポイントの衝突の結果として表示されることを示します。  これは `MT_REASON_EXCEPTION` に相互に排他的です。  
  
 MT\_REASON\_MASK  
 表示されるメッセージの原因を特定するマスクの値。  
  
## 解説  
 これらの値は [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) と [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) のメソッドから返されます。  
  
 理由値の 1 つがを使用して出力の終了値の 1 と `OR` ビットごとにまとめることができます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)