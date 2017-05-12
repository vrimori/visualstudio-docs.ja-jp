---
title: "IProvideExpressionContexts インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProvideExpressionContexts インターフェイス"
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts インターフェイス
特定のコンポーネントによって認識される式のコンテキストを列挙する方法を示します。  スクリプト エンジンは通常、このインターフェイスを実装します。  
  
 プロセス デバッグ マネージャーは、特定のスレッドに関連付けられているすべてのグローバル コンテキスト式を検索するには、このインターフェイスを使用します。  
  
> [!NOTE]
>  このインターフェイスは、対象スレッド内から呼び出されます。  これは、現在のスレッドを識別し、適切な列挙子を返す実装する必要があります。  
  
## メソッド  
 `IUnknown` から継承するメソッドに加え、`IProvideExpressionContexts` インターフェイスは次のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|このコンポーネントによって認識される式のコンテキストの列挙子を返します。|