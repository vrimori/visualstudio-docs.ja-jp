---
title: ビジネス データ接続モデルの作成 |Microsoft Docs
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
ms.openlocfilehash: 68940d6e48f1f3a3e51017e1cc838976735de104
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930207"
---
# <a name="create-a-business-data-connectivity-model"></a>ビジネス データ接続モデルを作成します。
  ビジネス データ接続 (BDC) モデルを作成したり、Visual Studio を使用して、既存の BDC モデルをカスタマイズすることができます。 各 SharePoint プロジェクトには、モデルの 1 つだけ含めることができます。 詳細については、次を参照してください。 [SharePoint ビジネス データを統合](../sharepoint/integrating-business-data-into-sharepoint.md)します。  
  
## <a name="create-a-new-model"></a>新しいモデルを作成します。
 新しいモデルを作成するには、作成、 **Business Data Connectivity モデル**プロジェクトまたは追加を**Business Data Connectivity モデル**項目を**空の SharePoint プロジェクト**します。  
  
> [!NOTE]  
>  必要があります[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]コンピューターにインストールします。  
  
 Visual Studio では、プロジェクトにフォルダーを追加します。 このフォルダーの指定した名前には、 **Business Data Connectivity モデル**内の項目、**新しい項目の追加** ダイアログ ボックス。 新規に作成する場合**Business Data Connectivity モデル**プロジェクト、Visual Studio という名前のフォルダー **BdcModel1**します。  
  
 Visual Studio では、新しいフォルダーに、次のファイルが追加されます。  
  
|ファイル|説明|  
|----------|-----------------|  
|モデル定義ファイル|エンティティ、メソッド、基幹業務 (LOB) システム オブジェクト、およびその他のモデルを記述するメタデータを定義する XML が含まれています。<br /><br /> BDC デザイナーを使用してこのファイルのメタデータを修正**BDC エクスプ ローラー**、 **BDC メソッドの詳細**ウィンドウ、および**プロパティ**ウィンドウ。|  
|エンティティ サービス コード ファイル|取得、更新、および既定のエンティティのインスタンスを削除するメソッドが含まれています。|  
  
 エンティティのプロパティを定義するには、エンティティのコード ファイルを編集します。 詳細については、次を参照してください。[方法: エンティティ モデルを追加する](../sharepoint/how-to-add-an-entity-to-a-model.md)します。  
  
 取得、更新、およびエンティティのインスタンスを削除、エンティティ サービス コード ファイルにコードを追加します。 詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
 プロジェクトをコンパイルするときに、Visual Studio は、アセンブリを作成します。 プロジェクトのアセンブリにコードを追加するプロジェクトにその他の項目を追加しないことを確認します (例:**シーケンシャル ワークフロー**項目または**Web パーツ**項目)。 ソリューション パッケージがグローバル アセンブリ キャッシュにアセンブリをコピーしていないために、ソリューションをデプロイすると、そのアイテムのコードは実行されません。  ソリューション パッケージには、SharePoint で BDC データベースをのみに、アセンブリがデプロイされます。  
  
> [!NOTE]  
>  Visual Studio では、プロジェクトをデバッグするときに、ローカル コンピューター上の両方の場所にアセンブリをコピーします。  
  
## <a name="add-an-existing-model"></a>既存のモデルを追加します。
 SharePoint Designer などの他のツールを使用して作成されたモデルをインポートすることができます。 次の状況で、プロジェクトに既存のモデルをインポートすることができます。  
  
- 既に SharePoint サーバー ファームに配置されているモデルをカスタマイズします。  
  
- パッケージ化し、既存のモデルを複数の SharePoint サーバー ファームに展開します。  
  
  どちらの場合は、インポートするモデルで定義されている LOB システムには影響せず、期待どおりに機能し続けます。 既存のモデルを SharePoint プロジェクトを追加する Visual Studio を使用して、**既存項目の追加** ダイアログ ボックス。 詳細については、次を参照してください。[方法: SharePoint プロジェクトに既存の BDC モデル ファイルを追加](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)します。  
  
  .NET Framework アセンブリの型の LOB システムをインポートしたモデルに追加するにはでオプションを選択して、**追加の .NET アセンブリの LobSystem**します。 これにより、カスタム コードを記述し、デザイナーを使用して、インポートしたモデルのメタデータを定義することができます。  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: BDC モデルの作成](../sharepoint/how-to-create-a-bdc-model.md)|新しい BDC モデルを作成する方法を示します。|  
|[方法: SharePoint プロジェクトに既存の BDC モデル ファイルを追加](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|SharePoint プロジェクトに既存のモデルをインポートする方法を示します。|  
|[方法: リソース ファイルを使用して、ローカライズされた名前、プロパティ、およびアクセス許可を指定するには](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Web パーツまたは Web ページで、モデルが使用されるときに、モデルのメタデータとマージする文字列を提供する方法について説明します。|  
|[方法: BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|この機能にカスタム アセンブリを含める方法を示します。|  
  
 
