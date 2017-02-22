---
title: "IEnumCodePaths2 | Microsoft Docs"
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
  - "IEnumCodePaths2"
helpviewer_keywords: 
  - "IEnumCodePaths2 インターフェイス"
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはコード パスのリストを表します。  
  
## 構文  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)コード パスの一覧を表すにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 このインターフェイスを取得します [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)。  
  
## Vtable の順序でメソッド  
 次の表は `IEnumCodePaths2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|列挙体シーケンスのコード パスの指定した数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|列挙体シーケンスのコード パスの指定した数の要素をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
|[GetCount](../Topic/IEnumCodePaths2::GetCount.md)|列挙子のコード パスの数を取得します。|  
  
## 解説  
 コード パスはプログラムのブランチ点や関数呼び出しを表します。  コード パスではコードの実行の継続パスを表します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)