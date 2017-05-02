---
title: "IDebugDocumentContext インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentContext インターフェイス"
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugDocumentContext インターフェイス
デバッグ ドキュメントの部分の抽象的に表示されます。  テキスト ドキュメントでは、この表現は、文字位置のスコープで構成されます。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugDocumentContext` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|このコンテキストを含む文書を返します。|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|このドキュメントのコンテキストに関連付けられたコード コンテキストを列挙します。|