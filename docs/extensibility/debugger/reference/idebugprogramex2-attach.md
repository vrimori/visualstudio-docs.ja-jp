---
title: "IDebugProgramEx2::Attach | Microsoft Docs"
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
  - "IDebugProgramEx2::Attach"
helpviewer_keywords: 
  - "IDebugProgramEx2::Attach"
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラムでセッションを追加します。  
  
## 構文  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### パラメーター  
 `pCallback`  
 \[入力\] アタッチされたデバッグ エンジンはイベントを送信 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) コールバック関数を表すオブジェクト。  
  
 `dwReason`  
 \[入力\] アタッチ操作の理由を説明する [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) の列挙体の値。  
  
 `pSession`  
 \[入力\] プログラムにアタッチしているセッションを識別する値。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  このメソッドはプログラムが既にアタッチされている `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` を返す必要があります。  
  
## 解説  
 プログラムを含むポートは `pSession` でのセッションがプログラムにアタッチするかを確認するには値を使用できます。  たとえばポートに 1 人のデバッグ セッションがプロセスにアタッチする一度に確保したポートは同じセッションのプロセスの他のプログラムに既にアタッチされているかどうかを確認できます。  
  
> [!NOTE]
>  渡されたインターフェイス`pSession`このプログラムにアタッチしているマネージャーのデバッグ セッションを識別する値として扱う必要があります。; 指定されたインターフェイスのメソッドが機能しません。  
  
## 参照  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)