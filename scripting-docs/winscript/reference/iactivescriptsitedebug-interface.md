---
title: "IActiveScriptSiteDebug インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebug インターフェイス"
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug インターフェイス
ホストは、スマート ドキュメントの管理を実行し、デバッグに含めるように `IActiveScriptSiteDebug` のインターフェイスを実装します。  `IActiveScriptSite` のオブジェクトは、通常、`IActiveScriptSiteDebug` のインターフェイスの実装を提供します。  これがの場合、`IActiveScriptSiteDebug` のインターフェイスを取得するに `IActiveScriptSite::QueryInterface` のメソッドを呼び出します。  
  
 `IUnknown` から継承するメソッドに加え、`IActiveScriptSiteDebug` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|`IDebugCodeContext::GetSourceContext`に代行させるために言語エンジンによって使用されます。|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|このスクリプトのサイトに関連付けられたデバッグ アプリケーション オブジェクトを返します。|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|スクリプト ドキュメントを追加する必要があるアプリケーションのノードを取得します。|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|スマート ホストがランタイム エラーの処理方法を決定できるようにします。|