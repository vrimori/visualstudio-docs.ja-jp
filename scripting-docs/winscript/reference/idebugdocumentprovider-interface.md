---
title: "IDebugDocumentProvider インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentProvider インターフェイス"
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider インターフェイス
ドキュメントをオンデマンドでインスタンス化する手段です。  
  
## 解説  
 このドキュメントのインスタンスを生成するための間接的な方法:  
  
-   必要な場合は、ドキュメントを読み込むようにします。  
  
-   ドキュメント オブジェクトがデバッガーの IDE 内に含まれるようにします。  
  
-   同じドキュメント オブジェクトにアクセスする割り当ての複数の方法を示します。  
  
 これは、プロバイダーからドキュメントを区切り、プロバイダーで追加の実行時、コンテキスト情報を伝達することができます。  
  
 `IDebugDocumentInfo` から継承するメソッドに加え、`IDebugDocumentProvider` インターフェイスは次のメソッドを公開します。  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|既にあるドキュメントをインスタンス化します。|