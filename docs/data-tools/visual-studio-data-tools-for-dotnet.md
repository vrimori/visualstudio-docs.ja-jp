---
title: ".NET 用の visual Studio data tools |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: bc63c636d58bcde7aefeb7d35939008387bb6808
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="visual-studio-data-tools-for-net"></a>.NET 用の visual Studio data tools
Visual Studio と .NET Framework は、一緒に広範な API とツールのデータベースへの接続、メモリ内のデータのモデリングおよびユーザー インターフェイスでデータを表示するためのサポートを提供します。 データ アクセス機能を提供する .NET Framework のクラスと呼ばれる[ADO.NET](/dotnet/framework/data/adonet/index)です。 Visual Studio でのツールをデータと共に、ADO.NET 当初の目的、主にするリレーショナル データベースおよび XML をサポートします。 今日では、多くの NoSQL データベース仕入先、またはサード パーティは、ADO.NET プロバイダーを提供します。  
  
[.NET core](https://www.dotnetfoundation.org/netcore)データセットと関連する型を除く、ADO.NET をサポートしています。 .NET Core を対象となるオブジェクト リレーショナル マッピング (ORM) レイヤーを必要としていて使用[Entity Framework Core](https://docs.microsoft.com/ef/core/)です。  
  
次の図は、基本的なアーキテクチャの概略を示します。  
  
![ADO.NET のアーキテクチャ](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata ADO.NET のアーキテクチャ図")  
  
一般的なワークフローでは、これです。  
  
1.  開発またはテスト データベースをローカル コンピューターにインストールします。 参照してください[データベース システム、ツール、およびサンプルをインストールする](../data-tools/installing-database-systems-tools-and-samples.md)です。 Azure データ サービスを使用している場合、この手順は必要ではありません。  
  
2.  Visual Studio でデータベース (またはサービスまたはローカル ファイル) への接続をテストします。 参照してください[新しい接続を追加](../data-tools/add-new-connections.md)です。  
  
3.  (省略可能)生成し、新しいモデルを構成するには、ツールを使用します。 Entity Framework に基づくモデルとは、新しいアプリケーションの既定の推奨事項です。 どちらを使用すると、モデルは、アプリケーションが対話するデータ ソースです。 モデルは、データベースまたはサービスとアプリケーション間で論理的に位置します。  参照してください[新しいデータ ソースを追加](../data-tools/add-new-data-sources.md)です。  
  
4.  元のデータ ソースをドラッグして、**データ ソース**ウィンドウから指定した方法でユーザーにデータを表示するデータ バインド コードを生成する、Windows フォーム、ASP.NET、または Windows Presentation Foundation のデザイン画面にします。 参照してください[Visual Studio でのデータにコントロールをバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)です。  
  
5.  処理など、ビジネス ルール、検索、およびデータの検証、または基になるデータベースを公開するカスタムの機能を活用するためのカスタム コードを追加します。  
  
手順 3. を省略して、モデルを使用するのではなく、データベースに直接コマンドを発行する .NET アプリケーションをプログラムできます。 この場合、ここにある関連するドキュメントが表示されます: [ADO.NET](/dotnet/framework/data/adonet/index)です。 使用することもできます、データ ソース構成ウィザードとデザイナーを独自のオブジェクトのメモリし、それらのオブジェクトを UI コントロールをデータ バインドを設定するときにデータ バインド コードを生成することを注意してください。
  
## <a name="see-also"></a>関連項目
[Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)