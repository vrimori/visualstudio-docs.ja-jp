---
title: 'エラー: Web サーバーが要求されたリソース見つかりません |Microsoft Docs'
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
ms.openlocfilehash: 8769c84237d877f02b7c9d3d02c6391f9e955ff3
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100979"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>エラー : Web サーバーでは要求されたリソースを見つけられませんでした
セキュリティ上の考慮から、IIS が汎用エラーを返しました。  

考えられる原因の 1 つは、サーバーのセキュリティ構成です。 IIS 6.0 以前のバージョンでは、URLScan と呼ばれるアドオン プログラムを使用して、不適切で疑わしい要求を除外しました。 IIS 7.0 には、同じ目的の要求フィルターが組み込まれています。 いずれの場合も、要求フィルター処理の制限が厳しすぎると Visual Studio がサーバーをデバッグできないことがあります。  

このエラーのもう 1 つの考えられる原因は、IIS の W3SVC サービスが開始されていないことです。 このサービスが開始された (グレー表示)、[サービス] ウィンドウで確認してください (*services.msc*)。

このエラーの他多数の考えられる原因があります。 最も一般的な原因には、IIS のインストールまたは構成の問題、Web サイトの構成の問題、ファイル システムのアクセス許可の問題などがあります。 ブラウザーを使用してリソースへのアクセスを試すことができます。 IIS の構成方法に応じて、サーバーでローカル ブラウザーを使用して、または詳細なエラー メッセージを取得する IIS エラー ログを確認する必要があります。  
  
 IIS のトラブルシューティングの詳細については、次を参照してください。 [IIS Management and Administration](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration)します。  
  
## <a name="see-also"></a>関連項目  
 [エラー: Web サーバーが制限され、デバッグの有効化に必要な DEBUG 動詞をブロックしています](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)