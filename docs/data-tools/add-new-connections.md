---
title: "新しい接続を追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 06170174436f37713f20c708c439e79af4d90198
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2017
---
# <a name="add-new-connections"></a>新しい接続を追加します。

データベース、サービスへの接続をテストしを使用してデータベースの内容とスキーマを探索できます**サーバー エクスプ ローラー**、 **Cloud Explorer**、または**SQL Server オブジェクト エクスプ ローラー**. これらのウィンドウの機能は、ある程度が重複しています。 基本的な違いは次のとおりです。

- サーバー エクスプローラー

   Visual Studio で既定でインストールします。 接続をテストし、SQL Server データベース、ADO.NET プロバイダーがインストールされているその他のデータベースおよび一部の Azure サービスを表示するために使用します。 システムのパフォーマンス カウンター、イベント ログ、およびメッセージ キューなどの低レベルのオブジェクトも示しています。 ADO.NET プロバイダー データ ソースがない場合は、ここでは、表示ことはありませんをそのまま使用する Visual Studio からプログラムで接続することで。

- Cloud Explorer

   このウィンドウを手動でインストール、Visual Studio 拡張機能を選択して**ツール**、**拡張機能と更新**、**オンライン**、 **Visual Studio Markeplace**. データの探索および Azure サービスに接続するには、特殊な機能を提供します。

- SQL Server オブジェクト エクスプローラー

   SQL Server Data Tools のインストールされ、下に表示される、**ビュー**メニュー。 表示されない場合がありますに移動**プログラムと機能**コントロール パネルで、Visual Studio を検索し、**変更**を SQL Server Data Tools のチェック ボックスを選択したら、インストーラーを再実行します。 使用して**SQL Server オブジェクト エクスプ ローラー** (ADO.NET プロバイダーがある) 場合は SQL データベースをビューに新しいデータベースを作成、スキーマ変更、ストアド プロシージャを作成、接続文字列を取得、データ、および詳細を表示します。 インストールされている ADO.NET プロバイダーがない SQL データベースはここでは、表示されませんが、接続できることをプログラムでします。

## <a name="add-a-connection-in-server-explorer"></a>サーバー エクスプ ローラーで、接続を追加します。

データベースへの接続を作成する をクリックして、**接続の追加**アイコン**サーバー エクスプ ローラー**、内を右クリックしてまたは**サーバー エクスプ ローラー**上、**データ接続**ノード**接続の追加**です。 ここでは、また別のサーバー、SharePoint サービス、または Azure サービス上のデータベースに接続することができます。

![サーバー エクスプ ローラーの新しい接続 アイコン](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata サーバー エクスプ ローラーの新しい接続 アイコン")

これにより、**接続の追加** ダイアログ ボックス。 ここでは、SQL Server LocalDB インスタンスの名前を入力しています。  

![新しい接続を追加](../data-tools/media/raddata-add-new-connection-dialog.png "raddata 新しい接続の追加ダイアログ")  

## <a name="change-the-provider"></a>プロバイダーを変更します。

データ ソースが必要ない場合をクリックして、**変更** ボタンを新しいデータ ソースや新しい ADO.NET データ プロバイダーを選択します。 新しいプロバイダーが構成方法に応じて、資格情報を要求します。

![AD0.NET データ プロバイダーを変更する](../data-tools/media/raddata-change-ad0.net-data-provider.png "raddata AD0.NET データ プロバイダーの変更")

## <a name="test-the-connection"></a>接続をテストします

データ ソースを選択した後にをクリックして**Test-connection**です。 成功しなかった場合必要がありますをトラブルシューティングするベンダーのドキュメントに基づく。

![接続をテストする](../data-tools/media/raddata-test-connection.png "raddata 接続のテスト")

作成する準備ができたら、テストが成功した場合、*データ ソース*、本当にことを意味している Visual Studio 用語は、*データ モデル*基になるデータベースまたはサービスに基づきます。

## <a name="see-also"></a>関連項目

[.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)