---
title: "IEnumDebugModules2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugModules2"
helpviewer_keywords: 
  - "IEnumDebugModules2"
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはモジュールのリストを列挙します。  
  
## 構文  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはプログラム \(DE\) に読み込まれたモジュールの一覧を表すにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 Visual Studio はこのインターフェイスを取得するに [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugModules2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|列挙体シーケンス内の指定したモジュールの数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|列挙体シーケンス内のモジュールの指定した数の要素をスキップします。|  
|[リセット](../Topic/IEnumDebugModules2::Reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|モジュールの数を取得します。|  
  
## 解説  
 Visual Studio には\[ENT0ENT\] ウィンドウを更新するにはこのインターフェイスを主に使用します。  
  
 Visual Studio のデバッグではプログラムをモジュールの境界を越えるできるコード命令の論理的な順序とそのため [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) の一つのインターフェイスのモジュールのリストに必要です。  リストの最初のモジュールは関連するプログラムの最初のエントリ ポイントが含まれています。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)