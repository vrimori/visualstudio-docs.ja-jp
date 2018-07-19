---
title: .NET 用の Visual Studio データ ツール
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
ms.openlocfilehash: 7a0df2adbb5dfb6a3ac8fa1c6312784bb6fa6768
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174027"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET 用の Visual Studio データ ツール

Visual Studio と .NET Framework は、さら広範な API とツールのデータベースへの接続、メモリ内のデータのモデリング、およびユーザー インターフェイスにデータを表示するためのサポートを提供します。 データ アクセス機能を提供する .NET Framework クラスと呼ばれます[ADO.NET](/dotnet/framework/data/adonet/index)します。 Visual Studio で、ツール、データと共に、ADO.NET は、リレーショナル データベースと XML をサポートするには、主に設計されています。 最近は、多くの NoSQL データベース ベンダー、または、第三者の ADO.NET プロバイダーを提供します。

[.NET core](/dotnet/core/)データセットおよび関連する型を除く、ADO.NET をサポートしています。 .NET Core をターゲットにして、オブジェクト リレーショナル マッピング (ORM) レイヤーを必要とする場合は、使用[Entity Framework Core](/ef/core/)します。

次の図は、基本的なアーキテクチャの概略を示します。

![ADO.NET のアーキテクチャ](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>一般的なワークフロー

一般的なワークフローは、

1. 開発またはテスト データベースをローカル コンピューターにインストールします。 参照してください[データベース システム、ツール、およびサンプルをインストールする](../data-tools/installing-database-systems-tools-and-samples.md)します。 Azure データ サービスを使用している場合、この手順は必要ではありません。

2. Visual Studio でのデータベース (またはサービスまたはローカル ファイル) への接続をテストします。 参照してください[新しい接続を追加](../data-tools/add-new-connections.md)します。

3. (省略可能)生成し、新しいモデルを構成するには、ツールを使用します。 Entity Framework に基づくモデルは、新しいアプリケーションの既定の推奨事項です。 どちらを使用すると、モデルは、アプリケーションと連携するデータ ソースです。 モデルは、データベースまたはサービスとアプリケーションの間に論理的にします。 参照してください[新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)します。

4. ドラッグ元のデータ ソース、**データ ソース**ウィンドウを指定した方法でユーザーに、データを表示するデータ バインド コードを生成する Windows フォーム、ASP.NET、または Windows Presentation Foundation デザイン サーフェイスにします。 参照してください[Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。

5. 点など、ビジネス ルール、検索、およびデータの検証、または基になるデータベースを公開するカスタム機能を活用するためのカスタム コードを追加します。

手順 3. を省略し、モデルを使用するのではなく、データベースに直接コマンドを発行する .NET アプリケーションをプログラミングできます。 この場合は、ここで、関連するドキュメントが表示されます: [ADO.NET](/dotnet/framework/data/adonet/index)します。 使用することもできますが、**データ ソース構成ウィザード**とメモリとし、それらのオブジェクトを UI コントロールをデータ バインドで、独自のオブジェクトの値を設定する際に、データ バインド コードを生成するデザイナー。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)