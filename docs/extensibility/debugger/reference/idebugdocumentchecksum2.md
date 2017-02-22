---
title: "IDebugDocumentChecksum2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDocumentChecksum2 インターフェイス"
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグに関連するドキュメントのチェックサムを表しコンポーネント間のチェックサムの受け渡しを有効にします。  
  
## 構文  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスは [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) インターフェイスを公開する任意のコンポーネントによって実行できます。  ただしデバッグ エンジンによって主にソースを検索するときにシンボル ファイル \(\*.pdb\) に埋め込まれたチェックサムが IDE に渡され使用できるように実行されます。  
  
## メソッド  
 次の表は `IDebugDocumentChecksum2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|使用する最大バイト数が含まれるドキュメントのとチェックサム アルゴリズム識別子を取得します。|  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll