---
title: "IApplicationDebuggerUI インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IApplicationDebuggerUI インターフェイス"
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI インターフェイス
外部コンポーネントにデバッガーのユーザー インターフェイス \(UI\) の詳細に制御できるようにデバッガーの統合開発環境 \(IDE\) によって実装される \( `IApplicationDebugger`に\)。  
  
 `IUnknown` から継承するメソッドに加え、`IApplicationDebuggerUI` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|デバッガーのユーザー インターフェイスにデバッグ指定のドキュメントを含む上にウィンドウが表示されます。|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|デバッガーのユーザー インターフェイスに特定の文書の先頭にコンテキストを含むウィンドウを取り込み、コンテキストにウィンドウをスクロールします。|