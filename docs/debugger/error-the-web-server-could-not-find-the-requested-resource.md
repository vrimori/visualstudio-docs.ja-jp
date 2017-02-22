---
title: "エラー : Web サーバーでは要求されたリソースを見つけられませんでした | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッガー, Web アプリケーション エラー"
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー : Web サーバーでは要求されたリソースを見つけられませんでした
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

セキュリティ上の考慮から、IIS が汎用エラーを返しました。  
  
 考えられる原因の 1 つは、サーバーのセキュリティ構成です。  IIS 6.0 以前のバージョンでは、URLScan と呼ばれるアドオン プログラムを使用して、不適切で疑わしい要求を除外しました。  IIS 7.0 には、同じ目的の要求フィルターが組み込まれています。  いずれの場合も、要求フィルター処理の制限が厳しすぎると Visual Studio がサーバーをデバッグできないことがあります。  
  
 このエラーには、さまざまな原因が考えられます。  最も一般的な原因には、IIS のインストールまたは構成の問題、Web サイトの構成の問題、ファイル システムのアクセス許可の問題などがあります。  ブラウザーを使用してリソースへのアクセスを試すことができます。  IIS の構成方法によっては、サーバーでローカル ブラウザーを使用したり、IIS エラー ログを検査して詳細なエラー メッセージを確認したりする必要があります。  
  
 IIS のトラブルシューティングの詳細については、「[IIS Management and Administration \(IIS の管理\)](http://go.microsoft.com/fwlink/?LinkId=255872)」を参照してください。  
  
## 参照  
 [URLScan セキュリティ ツール](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [エラー ： Web サーバーが制限され、デバッグの有効化に必要な DEBUG 動詞をブロックしています。](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)