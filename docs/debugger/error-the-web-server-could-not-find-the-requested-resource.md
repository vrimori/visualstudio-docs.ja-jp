---
title: エラー :Web サーバーで要求されたリソースが見つかりませんでした |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cba31527af469b897ae178b6b0f810840b7d9cd2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035485"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>エラー :Web サーバーでは要求されたリソースを見つけられませんでした
セキュリティ上の考慮から、IIS が汎用エラーを返しました。  

考えられる原因の 1 つは、サーバーのセキュリティ構成です。 IIS 6.0 以前のバージョンでは、URLScan と呼ばれるアドオン プログラムを使用して、不適切で疑わしい要求を除外しました。 IIS 7.0 には、同じ目的の要求フィルターが組み込まれています。 いずれの場合も、要求フィルター処理の制限が厳しすぎると Visual Studio がサーバーをデバッグできないことがあります。  

このエラーのもう 1 つの考えられる原因は、IIS の W3SVC サービスが開始されていないことです。 このサービスが開始された (グレー表示)、[サービス] ウィンドウで確認してください (*services.msc*)。

このエラーの他多数の考えられる原因があります。 最も一般的な原因には、IIS のインストールまたは構成の問題、Web サイトの構成の問題、ファイル システムのアクセス許可の問題などがあります。 ブラウザーを使用してリソースへのアクセスを試すことができます。 IIS の構成方法によっては、サーバー上でローカル ブラウザーを使用したり、IIS エラー ログを検査して詳細なエラー メッセージを確認したりする必要があります。  
  
 IIS のトラブルシューティングの詳細については、「[IIS Management and Administration (IIS の管理)](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration)」を参照してください。  
  
## <a name="see-also"></a>関連項目
 [エラー: Web サーバーが制限され、デバッグの有効化に必要な DEBUG 動詞をブロックしています](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
