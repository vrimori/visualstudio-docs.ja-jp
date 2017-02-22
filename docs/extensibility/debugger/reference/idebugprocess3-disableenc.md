---
title: "IDebugProcess3::DisableENC | Microsoft Docs"
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
  - "IDebugProcess3::DisableENC"
helpviewer_keywords: 
  - "IDebugProcess3::DisableENC"
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは明示的に編集を無効にし格納されているすべてのプログラムこのプロセスを続行します。  カスタム ポートの業者は `E_NOTIMPL` を常に返す必要です。  
  
## 構文  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```c#  
   EncUnavailableReason reason  
);  
```  
  
#### パラメーター  
 `reason`  
 \[入力\] [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) の列挙体の値。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
> [!NOTE]
>  カスタム ポートの業者は `E_NOTIMPL` を常に返す必要です。  
  
## 解説  
 一度エディット コンティニュはプロセスのプロセスの再起動によってのみ無効になります。再び有効にできます。  
  
## 参照  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)