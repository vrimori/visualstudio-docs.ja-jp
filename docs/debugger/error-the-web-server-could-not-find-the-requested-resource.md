---
title: 'エラー: Web サーバー見つかりません、要求されたリソース |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48d4a5845dd5e5f364d34544f57e1ef7bdfe6052
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>エラー : Web サーバーでは要求されたリソースを見つけられませんでした
セキュリティ上の考慮から、IIS が汎用エラーを返しました。  
  
 考えられる原因の 1 つは、サーバーのセキュリティ構成です。 IIS 6.0 以前のバージョンでは、URLScan と呼ばれるアドオン プログラムを使用して、不適切で疑わしい要求を除外しました。 IIS 7.0 には、同じ目的の要求フィルターが組み込まれています。 いずれの場合も、要求フィルター処理の制限が厳しすぎると Visual Studio がサーバーをデバッグできないことがあります。  
  
 このエラーには、さまざまな原因が考えられます。 最も一般的な原因には、IIS のインストールまたは構成の問題、Web サイトの構成の問題、ファイル システムのアクセス許可の問題などがあります。 ブラウザーを使用してリソースへのアクセスを試すことができます。 IIS の構成方法によっては、サーバーでローカル ブラウザーを使用したり、IIS エラー ログを検査して詳細なエラー メッセージを確認したりする必要があります。  
  
 IIS のトラブルシューティングの詳細については、次を参照してください。 [IIS 管理](http://go.microsoft.com/fwlink/?LinkId=255872)です。  
  
## <a name="see-also"></a>関連項目  
 [UrlScan セキュリティ ツール](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [エラー: Web サーバーが制限され、デバッグの有効化に必要な DEBUG 動詞をブロックしています](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)