---
title: '方法: BDC モデルの作成 |Microsoft Docs'
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
ms.openlocfilehash: 1a0e2bc47c902707ee896c46fa0d9988551fa6fd
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757923"
---
# <a name="how-to-create-a-bdc-model"></a>方法: BDC モデルの作成
  ビジネス データ接続 (BDC: Business Data Connectivity) モデルを作成するには、アイテムの種類に対応するテンプレートを使用し、モデルを任意の SharePoint プロジェクトに追加します。 詳細については、次を参照してください。 [business data connectivity モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)です。 モデルを設計する方法の詳細については、次を参照してください。[ビジネス データ接続モデルを設計する](../sharepoint/designing-a-business-data-connectivity-model.md)します。  
  
### <a name="to-create-a-bdc-project"></a>BDC プロジェクトを作成するには  
  
1.  メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。  
  
    > [!NOTE]  
    >  お使いの IDE が Visual Basic 開発設定を使用する設定、**ファイル** > **新しいプロジェクト**します。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  いずれかで**Visual Basic**または**Visual c#**、選択**Office/sharepoint**、 **SharePoint ソリューション**します。  
  
3.  **テンプレート**ウィンドウで、選択、 **SharePoint 2013 - 空のプロジェクト**項目を選び、 **OK**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が開きます。  
  
4.  **デバッグのサイトとセキュリティのレベルを指定**] ページで、ローカル コンピューター上の SharePoint サイトの URL を指定する、選択、**ファーム ソリューションとして配置**オプション、ボタンをクリックし、[、 **完了**ボタンをクリックします。  
  
     指定した SharePoint サイトでモデルをテストします。  
  
    > [!IMPORTANT]  
    >  BDC モデルはファーム ソリューションのみサポートするため、プロジェクトはファーム ソリューションとして配置する必要があります。  
  
     空の SharePoint プロジェクトが作成されます。  
  
5.  メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。  
  
6.  **新しい項目の追加** ダイアログ ボックスで、選択、 **Office/sharepoint**ノード。  
  
7.  SharePoint テンプレートの一覧で選択**ビジネス データ接続モデル (ファーム ソリューションのみ)** します。  
  
8.  **名前**ボックス、BDC モデルの名前を指定し、選択、**追加**ボタンをクリックします。  
  
     A **Business Data Connectivity モデル**項目がプロジェクトに追加します。 既定で、BDC デザイナーにモデルが表示されます。 詳細については、次を参照してください。 [business data connectivity モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
## <a name="see-also"></a>関連項目
 [ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [方法: SharePoint プロジェクトに既存の BDC モデル ファイルを追加](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [方法: リソース ファイルを使用して、ローカライズされた名前、プロパティ、およびアクセス許可を指定するには](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [方法: BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [SharePoint にビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
