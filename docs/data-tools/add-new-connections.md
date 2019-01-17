---
title: 新しい接続を追加する
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 73b09384bd57fd4ea0890d107ce641e4b615559f
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154219"
---
# <a name="add-new-connections"></a>新しい接続を追加する

データベース、サービスへの接続をテストして使用してデータベースの内容とスキーマを調べる、**サーバー エクスプ ローラー**、 **Cloud Explorer**、または**SQL Server オブジェクト エクスプ ローラー**. これらのウィンドウの機能は、ある程度重複しています。 基本的な違いは次のとおりです。

- サーバー エクスプローラー

   Visual Studio で既定でインストールします。 接続をテストし、SQL Server データベース、ADO.NET プロバイダーがインストールされている他のデータベースおよび一部の Azure サービスを表示するために使用します。 システム パフォーマンス カウンター、イベント ログ、メッセージ キューなどの低レベルのオブジェクトとも表示されます。 ADO.NET プロバイダー データ ソースがない場合は、ここでは、表示されませんはそのまま使用する Visual Studio からプログラムで接続することで。

- Cloud Explorer

   このウィンドウを Visual Studio 拡張機能として手動でインストールを選択して**ツール** > **拡張機能と更新** > **オンライン** >  **Visual Studio Marketplace**します。 探索と Azure サービスに接続するのには、特殊な機能を提供します。

- SQL Server オブジェクト エクスプローラー

   SQL Server Data Tools でインストールされ、下に表示される、**ビュー**メニュー。 場合は、表示がない場合は、**プログラムと機能**コントロール パネルで、Visual Studio を検索し、**変更**を SQL Server Data Tools のチェック ボックスを選択したら、インストーラーを再実行します。 使用**SQL Server オブジェクト エクスプ ローラー** (ADO.NET プロバイダーがある) 場合は SQL データベースをビューに新しいデータベースを作成、スキーマの変更、ストアド プロシージャを作成、接続文字列を取得、データ、および詳細を表示します。 インストールされている ADO.NET プロバイダーがない SQL データベースはここでは、表示されませんが、プログラムでそれらに接続することができますもします。

## <a name="add-a-connection-in-server-explorer"></a>サーバー エクスプ ローラーの接続を追加します。

データベースへの接続を作成する をクリックして、**接続の追加**アイコン**サーバー エクスプ ローラー**を右クリックしてまたは**サーバー エクスプ ローラー**上、**データ接続**ノード**接続の追加**します。 ここでは、別のサーバー、SharePoint サービス、または Azure サービス上のデータベースにも接続できます。

![サーバー エクスプ ローラーの新しい接続 アイコン](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

すると、**接続の追加** ダイアログ ボックス。 ここでは、SQL Server LocalDB インスタンスの名前を入力しています。

![新しい接続を追加する](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>プロバイダーを変更します。

データ ソースが必要ない場合は、クリックして、**変更**新しいデータ ソースや新しい ADO.NET データ プロバイダーを選択するボタンをクリックします。 新しいプロバイダーがその構成方法に応じて、資格情報を要求します。

![AD0.NET データ プロバイダーの変更](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>接続をテストする

データ ソースを選択した後にをクリックして**Test-connection**します。 成功しなかった場合はトラブルシューティングが必要なベンダーのドキュメントに基づいて。

![テスト接続](../data-tools/media/raddata-test-connection.png)

作成する準備が完了したら、テストが成功した場合、*データ ソース*、つまり本当に Visual Studio という用語は、*データ モデル*基になるデータベースまたはサービスに基づきます。

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)
