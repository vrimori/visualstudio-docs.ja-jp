---
title: "ビジネス データ接続モデルの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio での SharePoint 開発], 作成 (モデルを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 作成 (モデルを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], モデル"
  - "Visual Studio での SharePoint 開発, ビジネス データ接続サービス"
ms.assetid: 19fd12d0-a51a-4da4-98ac-918542e84507
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# ビジネス データ接続モデルの作成
  Visual Studio を使用して、ビジネス データ接続 \(BDC\) モデルを作成したり、既存の BDC モデルをカスタマイズしたりすることができます。  各 SharePoint プロジェクトに含めることができるモデルは 1 つのみです。  詳細については、「[SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)」を参照してください。  
  
## 新しいモデルの作成  
 新しいモデルを作成するには、**ビジネス データ接続モデル** プロジェクトを作成するか、**ビジネス データ接続モデル**項目を**空の SharePoint プロジェクト**に追加します。  
  
> [!NOTE]  
>  コンピューターに [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] をインストールしておく必要があります。  
  
 プロジェクトにフォルダーが追加されます。  このフォルダーの名前は、**\[新しい項目の追加\]** ダイアログ ボックスで**ビジネス データ接続モデル**項目に指定した名前になります。  新しい**ビジネス データ接続モデル** プロジェクトを作成すると、**BdcModel1** という名前のフォルダーが追加されます。  
  
 次のファイルが新しいフォルダーに追加されます。  
  
|File|説明|  
|----------|--------|  
|モデル定義ファイル|モデルについて説明するエンティティ、メソッド、基幹業務 \(LOB\) システム オブジェクトなどのメタデータを定義する XML を含みます。<br /><br /> BDC デザイナー、**BDC エクスプローラー**、**\[BDC メソッドの詳細\]** ウィンドウ、および**プロパティ** ウィンドウを使用して、このファイルのメタデータを変更します。|  
|エンティティ サービス コード ファイル|既定のエンティティのインスタンスを取得、更新、および削除するメソッドを含みます。|  
  
 エンティティのプロパティを定義するには、エンティティ コード ファイルを編集します。  詳細については、「[方法: モデルにエンティティを追加する](../sharepoint/how-to-add-an-entity-to-a-model.md)」を参照してください。  
  
 エンティティのインスタンスを取得、更新、および削除するには、エンティティ サービス コード ファイルにコードを追加します。  詳細については、「[Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)」を参照してください。  
  
 プロジェクトをコンパイルすると、アセンブリが作成されます。  プロジェクト アセンブリにコードを追加するプロジェクトに、他の項目を追加しないでください \(**シーケンシャル ワークフロー**項目や **Web パーツ**項目など\)。  ソリューション パッケージはグローバル アセンブリ キャッシュにアセンブリをコピーしないため、ソリューションを配置してもこの項目のコードは実行されません。ソリューション パッケージは SharePoint の BDC データベースにのみアセンブリを配置します。  
  
> [!NOTE]  
>  プロジェクトをデバッグすると、ローカル コンピューター上の両方の場所にアセンブリがコピーされます。  
  
## 既存のモデルの追加  
 SharePoint デザイナーなど、他のツールを使用して作成したモデルをインポートできます。  次のような場合に、既存のモデルをプロジェクトにインポートすることもできます。  
  
-   SharePoint サーバー ファームへ既に配置されているモデルをカスタマイズする場合。  
  
-   既存のモデルをパッケージ化して複数の SharePoint サーバー ファームに配置する場合。  
  
 いずれの場合でも、インポートするモデルに定義されている LOB システムは影響を受けず、予定どおりに機能します。  SharePoint プロジェクトに既存のモデルを追加するには、Visual Studio の **\[既存項目の追加\]** ダイアログ ボックスを使用します。  詳細については、「[方法: 既存の BDC モデル ファイルを SharePoint プロジェクトに追加する](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)」を参照してください。  
  
 種類が .NET Framework アセンブリの LOB システムを、インポートしたモデルに追加するには、**\[.NET アセンブリの LobSystem を追加\]** でオプションを選択します。  その結果、カスタム コードを記述できるようになります。また、デザイナーを使用して、インポートしたモデルのメタデータを定義できます。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[方法: BDC モデルを作成する](../sharepoint/how-to-create-a-bdc-model.md)|新しい BDC モデルの作成方法について説明します。|  
|[方法: 既存の BDC モデル ファイルを SharePoint プロジェクトに追加する](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|既存のモデルを SharePoint プロジェクトにインポートする方法について説明します。|  
|[方法: リソース ファイルを使用して、ローカライズした名前、プロパティ、およびアクセス許可を指定する](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Web パーツまたは Web ページからモデルを使用するときに、モデルのメタデータとマージする文字列を指定する方法について説明します。|  
|[方法: BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|機能にカスタム アセンブリを含める方法について説明します。|  
  
  