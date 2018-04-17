---
title: ビジネス データ接続モデルを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f823c8c67750dec31c6c2b534ecc7500e20defaf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-business-data-connectivity-model"></a>ビジネス データ接続モデルの作成
  ビジネス データ接続 (BDC) モデルを作成したり、Visual Studio を使用して、既存の BDC モデルをカスタマイズすることができます。 各 SharePoint プロジェクトには、1 つのみのモデルを含めることができます。 詳細については、次を参照してください。 [SharePoint にビジネス データを統合する](../sharepoint/integrating-business-data-into-sharepoint.md)です。  
  
## <a name="creating-a-new-model"></a>新しいモデルを作成します。  
 新しいモデルを作成するには、作成、**ビジネス データ接続モデル**プロジェクトや追加、**ビジネス データ接続モデル**項目を**空の SharePoint プロジェクト**です。  
  
> [!NOTE]  
>  必要があります[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]コンピューターにインストールします。  
  
 Visual Studio では、プロジェクトにフォルダーを追加します。 指定した名前は、このフォルダーが、**ビジネス データ接続モデル**内の項目、**新しい項目の追加** ダイアログ ボックス。 新規に作成する場合**ビジネス データ接続モデル**プロジェクトを Visual Studio という名前のフォルダー **BdcModel1**です。  
  
 Visual Studio では、新しいフォルダーに、次のファイルを追加します。  
  
|ファイル|説明|  
|----------|-----------------|  
|モデル定義ファイル|エンティティ、メソッド、基幹業務 (LOB) システム オブジェクト、およびその他のモデルを記述するメタデータを定義する XML が含まれています。<br /><br /> BDC デザイナーを使用してこのファイル内のメタデータを変更**BDC エクスプ ローラー**、 **BDC メソッドの詳細**ウィンドウ、および**プロパティ**ウィンドウです。|  
|エンティティ サービス コード ファイル|取得、更新、および既定のエンティティのインスタンスを削除するメソッドが含まれています。|  
  
 エンティティのプロパティを定義するのには、エンティティのコード ファイルを編集します。 詳細については、次を参照してください。[する方法: エンティティをモデルに追加](../sharepoint/how-to-add-an-entity-to-a-model.md)です。  
  
 取得、更新、およびエンティティのインスタンスを削除、エンティティ サービス コード ファイルにコードを追加します。 詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
 プロジェクトをコンパイルするときに、Visual Studio は、アセンブリを作成します。 プロジェクトのアセンブリにコードを追加するプロジェクトに他の項目を追加しないことを確認してください (例:**シーケンシャル ワークフロー**項目または**Web パーツ**項目)。 ソリューション パッケージがグローバル アセンブリ キャッシュにアセンブリをコピーしないため、ソリューションを展開するときに、その項目のコードは実行されません。  ソリューション パッケージが、BDC データベースに SharePoint でのみ、アセンブリを展開します。  
  
> [!NOTE]  
>  Visual Studio では、プロジェクトをデバッグするときに、ローカル コンピューター上の両方の場所にアセンブリをコピーします。  
  
## <a name="adding-an-existing-model"></a>既存のモデルを追加します。  
 SharePoint Designer などその他のツールを使用して作成したモデルをインポートすることができます。 次の状況で、プロジェクトに既存のモデルをインポートを選択する場合があります。  
  
-   既に SharePoint サーバー ファームに配置されているモデルをカスタマイズします。  
  
-   パッケージ化して、既存のモデルを複数の SharePoint サーバー ファームに展開します。  
  
 どちらの場合、インポートするモデルで定義されている LOB システムには影響しません、期待どおりに動作し続けます 既存のモデルを SharePoint プロジェクトを追加するには、Visual Studio を使用**既存項目の追加** ダイアログ ボックス。 詳細については、次を参照してください。[する方法: SharePoint プロジェクトに既存の BDC モデル ファイルを追加](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)です。  
  
 型の .NET Framework アセンブリの LOB システムをインポートしたモデルに追加するにはのオプションを選択して、**追加の .NET アセンブリの LobSystem**です。 これにより、カスタム コードを記述し、デザイナーを使用して、インポートされたモデルのメタデータを定義することができます。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: BDC モデルを作成する](../sharepoint/how-to-create-a-bdc-model.md)|新しい BDC モデルを作成する方法を示します。|  
|[方法: 既存の BDC モデル ファイルを SharePoint プロジェクトに追加する](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|SharePoint プロジェクトに既存のモデルをインポートする方法を示します。|  
|[方法: リソース ファイルを使用して、ローカライズした名前、プロパティ、およびアクセス許可を指定する](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Web パーツまたは Web ページで、モデルが使用される場合、モデルのメタデータとマージする文字列を提供する方法について説明します。|  
|[方法: BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|この機能にカスタム アセンブリを含める方法を示します。|  
  
  