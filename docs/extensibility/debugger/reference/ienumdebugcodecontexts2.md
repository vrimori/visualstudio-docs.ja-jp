---
title: "IEnumDebugCodeContexts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugCodeContexts2"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2"
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションまたは特定のプログラムまたはドキュメントに関連付けられたコード コンテキストを列挙します。  
  
## 構文  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)このインターフェイス特定のドキュメントのコンテキストのプログラムの特定のテキストの位置のコード コンテキスト リストまたはコード コンテキストの一覧を表すために実装します。  
  
## 呼び出し元のメモ  
 プログラムのソース ドキュメントの特定のテキストの位置のコード コンテキストの一覧を表すこのインターフェイスを取得します [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)。  
  
 特定のソース ドキュメントのすべてのコード コンテキストの一覧を表すこのインターフェイスを取得するに [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) を呼び出します。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumDebugCodeContexts2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|列挙体シーケンスのコード コンテキストの指定された数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|列挙体シーケンス内のコードのコンテキストから指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|列挙子のコード コンテキストの数を取得します。|  
  
## 解説  
 Visual Studio はユーザーが選択できるコード コンテキストのリストに格納する [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) を呼び出します。次のステートメントを設定または表示するとソース ファイルの逆アセンブリ。  複数のコンテキスト . のコードはC\+\+ スタイル テンプレートの複数のインスタンスがある場合にこのエラーが発生します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)