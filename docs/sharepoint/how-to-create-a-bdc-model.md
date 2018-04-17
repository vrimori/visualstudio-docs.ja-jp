---
title: '方法: BDC モデルを作成 |Microsoft ドキュメント'
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
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aae6789d9961fa3cbf63ce073a33251465ee308a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-bdc-model"></a>方法: BDC モデルを作成する
  ビジネス データ接続 (BDC: Business Data Connectivity) モデルを作成するには、アイテムの種類に対応するテンプレートを使用し、モデルを任意の SharePoint プロジェクトに追加します。 詳細については、次を参照してください。[ビジネス データ接続モデルを作成する](../sharepoint/creating-a-business-data-connectivity-model.md)です。 モデルを設計する方法の詳細については、次を参照してください。[ビジネス データ接続モデルをデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)です。  
  
### <a name="to-create-a-bdc-project"></a>BDC プロジェクトを作成するには  
  
1.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
    > [!NOTE]  
    >  IDE が Visual Basic 開発設定を使用する設定、**ファイル**、**新しいプロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  いずれかで**Visual Basic**または**Visual c#**、選択**Office/sharepoint**、 **SharePoint ソリューション**です。  
  
3.  **テンプレート** ウィンドウで、選択、 **SharePoint 2013 - 空のプロジェクト**項目をクリックして、 **OK**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が開きます。  
  
4.  **デバッグのサイトとセキュリティ レベルを指定**] ページで、ローカル コンピューター上、SharePoint サイトの URL を指定して、選択、**ファーム ソリューションとして配置**オプションをクリックし、[、 **完了**ボタンをクリックします。  
  
     指定した SharePoint サイトでモデルをテストします。  
  
    > [!IMPORTANT]  
    >  BDC モデルはファーム ソリューションのみサポートするため、プロジェクトはファーム ソリューションとして配置する必要があります。  
  
     空の SharePoint プロジェクトが作成されます。  
  
5.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
6.  **新しい項目の追加** ダイアログ ボックスで、選択、 **Office/sharepoint**ノード。  
  
7.  SharePoint テンプレートの一覧で選択**ビジネス データ接続モデル (ファーム ソリューションのみ)**です。  
  
8.  **名前**ボックス、BDC モデルの名前を指定し、選択、**追加**ボタンをクリックします。  
  
     A**ビジネス データ接続モデル**項目は、プロジェクトに追加します。 既定で、BDC デザイナーにモデルが表示されます。 詳細については、次を参照してください。[ビジネス データ接続モデルを作成する](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [方法: SharePoint プロジェクトに既存の BDC モデル ファイルを追加](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [方法: リソース ファイルを使用して、ローカライズされた名前、プロパティ、およびアクセス許可](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [方法: BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  