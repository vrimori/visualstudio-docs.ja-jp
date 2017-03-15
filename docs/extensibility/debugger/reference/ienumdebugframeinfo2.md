---
title: "IEnumDebugFrameInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFrameInfo2"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2"
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) の構造を列挙します。  
  
## 構文  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)現在の呼び出し履歴を示す構造体のリストを作成するにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 Visual Studio では例外ブレークポイントまたは停止がデバッグ対象のプログラムに発生するたびにこのインターフェイスを取得するに [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugFrameInfo2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../Topic/IEnumDebugFrameInfo2::Next.md)|列挙体シーケンス内の指定 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) の構造体の数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|列挙体シーケンス内の [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 構造の指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../Topic/IEnumDebugFrameInfo2::GetCount.md)|列挙子の [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) の構造体の数を取得します。|  
  
## 解説  
 Visual Studio でプログラムのブレークポイント例外またはユーザー生成された一時停止の処理にこのインターフェイスはまず取得します。  [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) の構造体のリストはリストの先頭に現在の関数呼び出しとリストの最後にある最も古い関数呼び出しと現在の呼び出し履歴を表します。  各スタック フレーム `FRAMEINFO` は式が評価される確認しローカル変数コンテキストを表します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)