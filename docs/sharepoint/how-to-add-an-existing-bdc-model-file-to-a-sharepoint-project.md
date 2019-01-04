---
title: '方法: SharePoint プロジェクトに既存の BDC モデル ファイルの追加 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c9efe862fcd0844d6b6e0c050d4c647b2d9c705a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950122"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>方法: SharePoint プロジェクトに既存の BDC モデル ファイルを追加します。
  カスタマイズ、パッケージ化、および Visual Studio を使用してモデル ファイルを追加するビジネス データ接続 (BDC) モデルを再配置 (*.bdcm*) を SharePoint ファーム プロジェクト。 詳細については、次を参照してください。 [business data connectivity モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)です。  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>BDC モデル ファイルを SharePoint プロジェクトに追加するには  
  
1. **ソリューション エクスプ ローラー**、SharePoint プロジェクトのフォルダーを選択します。  
  
2. メニュー バーで、**プロジェクト** > **既存項目の追加**します。  
  
3. **既存項目の追加**ダイアログ ボックスで、プロジェクトに追加、ファイルを選択し、選択するモデル定義ファイルの場所を指定し、**追加**ボタンをクリックします。  
  
    モデルが定義されていない場合、 *.NET アセンブリの型の基幹業務 (LOB) システム*、**追加の .NET アセンブリの LobSystem**  ダイアログ ボックスが表示されます。  
  
4. ダイアログ ボックスが表示された場合は、次の手順のいずれかを実行します。  
  
   - カスタム コードを記述し、デザイナーを使用して、メタデータをインポートしたモデルの定義を選択する場合、**はい**ボタンをクリックし、システムの名前を選択し、 **OK**ボタン。  
  
   - それ以外の場合、選択、**いいえ**ボタンをクリックし、選択し、 **[ok]** ボタンをクリックします。  
  
     **Business Data Connectivity モデル**項目がプロジェクトに追加します。  
  
## <a name="see-also"></a>関連項目
 [ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [方法: BDC モデルを作成します。](../sharepoint/how-to-create-a-bdc-model.md)   
 [方法: リソース ファイルを使用して、ローカライズされた名前、プロパティ、およびアクセス許可を指定するには](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [方法: BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [SharePoint にビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
