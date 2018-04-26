---
title: .NET 用の visual Studio data tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: d2db4210085e3dc16d9c4b9e00653312ae0d5a82
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="visual-studio-data-tools-for-net"></a>.NET 用の visual Studio data tools

Visual Studio と .NET Framework は、一緒に広範な API とツールのデータベースへの接続、メモリ内のデータのモデリングおよびユーザー インターフェイスでデータを表示するためのサポートを提供します。 データ アクセス機能を提供する .NET Framework のクラスと呼ばれる[ADO.NET](/dotnet/framework/data/adonet/index)です。 Visual Studio でのツールをデータと共に、ADO.NET 当初の目的、主にするリレーショナル データベースおよび XML をサポートします。 今日では、多くの NoSQL データベース仕入先、またはサード パーティは、ADO.NET プロバイダーを提供します。

[.NET core](/dotnet/core/)データセットと関連する型を除く、ADO.NET をサポートしています。 .NET Core を対象となるオブジェクト リレーショナル マッピング (ORM) レイヤーを必要としていて使用[Entity Framework Core](/ef/core/)です。

次の図は、基本的なアーキテクチャの概略を示します。

![ADO.NET のアーキテクチャ](../data-tools/media/raddata-ado-net-architecture-diagram.png)

一般的なワークフローでは、これです。

1. 開発またはテスト データベースをローカル コンピューターにインストールします。 参照してください[データベース システム、ツール、およびサンプルをインストールする](../data-tools/installing-database-systems-tools-and-samples.md)です。 Azure データ サービスを使用している場合、この手順は必要ではありません。

2. Visual Studio でデータベース (またはサービスまたはローカル ファイル) への接続をテストします。 参照してください[新しい接続を追加](../data-tools/add-new-connections.md)です。

3. (省略可能)生成し、新しいモデルを構成するには、ツールを使用します。 Entity Framework に基づくモデルとは、新しいアプリケーションの既定の推奨事項です。 どちらを使用すると、モデルは、アプリケーションが対話するデータ ソースです。 モデルは、データベースまたはサービスとアプリケーション間で論理的に位置します。 参照してください[新しいデータ ソースを追加](../data-tools/add-new-data-sources.md)です。

4. 元のデータ ソースをドラッグして、**データ ソース**ウィンドウから指定した方法でユーザーにデータを表示するデータ バインド コードを生成する、Windows フォーム、ASP.NET、または Windows Presentation Foundation のデザイン画面にします。 参照してください[Visual Studio でのデータにコントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)です。

5. 処理など、ビジネス ルール、検索、およびデータの検証、または基になるデータベースを公開するカスタムの機能を活用するためのカスタム コードを追加します。

手順 3. を省略して、モデルを使用するのではなく、データベースに直接コマンドを発行する .NET アプリケーションをプログラムできます。 この場合、ここにある関連するドキュメントが表示されます: [ADO.NET](/dotnet/framework/data/adonet/index)です。 使用することもできます、データ ソース構成ウィザードとデザイナーを独自のオブジェクトのメモリし、それらのオブジェクトを UI コントロールをデータ バインドを設定するときにデータ バインド コードを生成することを注意してください。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)