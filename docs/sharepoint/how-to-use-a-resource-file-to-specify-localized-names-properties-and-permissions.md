---
title: '方法: リソース ファイルを使用して、ローカライズされた名前、プロパティ、およびアクセス許可 |Microsoft ドキュメント'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58c8d74e29144a525eb33031fb98e25051d0305f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>方法: リソース ファイルを使用して、ローカライズした名前、プロパティ、およびアクセス許可を指定する
  リソース ファイルを使用すると、ローカライズされた名前を指定、プロパティを定義でき、ビジネス データ接続 (BDC) モデルで定義されているアクセス許可 tor オブジェクトに適用できます。 この情報を指定するを追加する、**ビジネス データ接続リソース**項目を含むプロジェクトを**ビジネス データ接続モデル**項目。 次のリソース ファイルの XML を編集して名、プロパティ、およびアクセス許可を指定します。  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>BDC リソース ファイルを SharePoint プロジェクトに追加するには  
  
1.  **ソリューション エクスプ ローラー**、SharePoint プロジェクトのフォルダーを展開し、BDC モデルを含むフォルダーを選択します。  
  
2.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
3.  展開して、 **SharePoint**  ノードを選択し、 **2010**ノード。  
  
4.  **新しい項目の追加** ダイアログ ボックスで、選択**ビジネス データ接続リソース項目**です。  
  
5.  **名前**ボックス、リソース ファイルの名前を指定し、選択、**追加**ボタンをクリックします。  
  
     .Bdcr 拡張子を持つリソース ファイルがプロジェクトに追加され、編集用に開きます。  
  
6.  ローカライズされた名前、プロパティ、および、BDC モデルを適用するアクセス許可を定義する XML を追加します。  
  
     これらの要素を定義する方法については、次を参照してください。[モデル ファイルとリソース ファイル](http://go.microsoft.com/fwlink/?LinkID=169283)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: SharePoint プロジェクトに既存の BDC モデル ファイルを追加](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [方法: BDC モデルを作成](../sharepoint/how-to-create-a-bdc-model.md)   
 [方法: BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  