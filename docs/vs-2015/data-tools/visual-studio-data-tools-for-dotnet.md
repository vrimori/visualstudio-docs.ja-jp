---
title: .NET 用の visual Studio データ ツール |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 841311af90ddf4bedfb9d055e5764068cdc71632
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859708"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET 用の Visual Studio データ ツール
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio と .NET Framework は、さら広範な API とツールのデータベースへの接続、メモリ内のデータのモデリング、およびユーザー インターフェイスにデータを表示するためのサポートを提供します。  データ アクセス機能を提供する .NET Framework クラスと呼ばれます[ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx)します。 Visual Studio で、ツール、データと共に、ADO.NET は、リレーショナル データベースと XML をサポートするには、主にもともと設計されています。 最近は、多くの NoSQL データベース ベンダー、または、第三者の ADO.NET プロバイダーを提供します。  
  
 Visual Studio 2015 Update 2 には最新の更新プログラムが含まれています[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)、Azure での最新機能のサポートを有効にする[SQL Database](https://azure.microsoft.com/en-us/services/sql-database/)と[SQL Server 2016](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/). [.NET core](https://www.dotnetfoundation.org/netcore)データセットおよび関連する型を除く、ADO.NET をサポートしています。 .NET Core をターゲットにして、オブジェクト リレーショナル マッピング (ORM) レイヤーを必要とする場合は、使用[Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx)します。  
  
 次の図は、基本的なアーキテクチャの概略を示します。  
  
 ![ADO.NET のアーキテクチャ](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata ADO.NET のアーキテクチャ図")  
  
 一般的なワークフローは、  
  
1. 開発またはテスト データベースをローカル コンピューターにインストールします。 参照してください[データベース システム、ツール、およびサンプルをインストールする](../data-tools/installing-database-systems-tools-and-samples.md)します。 Azure データ サービスを使用している場合、この手順は必要ではありません。  
  
2. Visual Studio でのデータベース (またはサービスまたはローカル ファイル) への接続をテストします。 参照してください[新しい接続を追加](../data-tools/add-new-connections.md)します。  
  
3. (省略可能)生成し、新しいモデルを構成するには、ツールを使用します。 Entity Framework に基づくモデルは、新しいアプリケーションの既定の推奨事項です。 どちらを使用すると、モデルは、アプリケーションと対話するデータ ソースです。 モデルは、データベースまたはサービスとアプリケーションの間に論理的にします。  参照してください[新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)します。  
  
4. ドラッグ元のデータ ソース、**データ ソース**ウィンドウを指定した方法でユーザーに、データを表示するデータ バインド コードを生成する Windows フォーム、ASP.NET、または Windows Presentation Foundation デザイン サーフェイスにします。 参照してください[Visual Studio でのデータ コントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)します。  
  
5. 点など、ビジネス ルール、検索、およびデータの検証、または基になるデータベースを公開するカスタム機能を活用するためのカスタム コードを追加します。  
  
   手順 3. を省略し、モデルを使用するのではなく、データベースに直接コマンドを発行する .NET アプリケーションをプログラミングできます。 この場合は、ここで、関連するドキュメントが表示されます: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx)します。 使用することもできる、データ ソース構成ウィザードとデザイナー メモリとし、それらのオブジェクトを UI コントロールをデータ バインドで、独自のオブジェクトの値を設定する際に、データ バインド コードを生成するに注意してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ADO.NET を使用した単純なデータ アプリケーションの作成](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
-   [新しい接続の追加](../data-tools/add-new-connections.md)  
  
-   [新しいデータ ソースの追加](../data-tools/add-new-data-sources.md)  
  
-   [Visual Studio のエンティティ データ モデル ツール](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
-   [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)  
  
-   [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
  
-   [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
-   [データ アクセス エラーのトラブルシューティングのための追加のリソース](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
-   [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
-   [Visual Studio でのデータベースおよびデータ層アプリケーションの作成と管理](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
-   [データ アクセス エラーのトラブルシューティングのための追加のリソース](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)







