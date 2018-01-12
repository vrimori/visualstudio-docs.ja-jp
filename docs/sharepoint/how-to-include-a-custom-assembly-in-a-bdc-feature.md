---
title: "方法: BDC 機能にカスタム アセンブリを含める |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 32554a0456c34a3c8b1d96c471fd7ae8e9221943
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>方法: BDC 機能にカスタム アセンブリを含める
  プロジェクトは、同じソリューション内の他のプロジェクトからアセンブリを参照できます。 使用して、プロジェクトのフィーチャー ファイルにこれらのアセンブリを追加する必要があります、**参照されるアセンブリの LobSystems への割り当て** ダイアログ ボックス。  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>ビジネス データ接続 (BDC) 機能にカスタム アセンブリを含める  
  
1.  **ソリューション エクスプ ローラー**、BDC モデルを含むフォルダーを選択します。  
  
2.  **[表示]** メニューの **[プロパティ ウィンドウ]**をクリックします。  
  
3.  **プロパティ**ウィンドウで、選択、**アセンブリ**プロパティ、し、省略記号ボタン (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイルデザイナー楕円"))。  
  
     **参照されるアセンブリの LobSystems への割り当て** ダイアログ ボックスが表示されます。  
  
4.  **アセンブリを選択して**一覧で、カスタム アセンブリを選択します。  
  
    > [!NOTE]  
    >  アセンブリにのみ表示されます、**参照されるアセンブリの LobSystems への割り当て**ダイアログ ボックスで、アセンブリを含むプロジェクトへの参照を追加した場合。 詳細については、次を参照してください。[する方法: 追加または参照の追加 ダイアログ ボックスを使用して参照を削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)です。  
  
5.  **参照プロパティ**グループで、について表示されるリストを開く、 **LobSystem スコープ**プロパティを選択し、カスタム アセンブリを使用して、メソッドの LOB システムを選択して、 **[ok]**ボタンをクリックします。  
  
    > [!NOTE]  
    >  カスタム アセンブリ内のコードをデバッグするには、ソリューション パッケージをアセンブリを追加する必要があります。 詳細については、次を参照してください。[する方法: 追加およびその他のアセンブリを削除する](../sharepoint/how-to-add-and-remove-additional-assemblies.md)です。  
  
## <a name="see-also"></a>参照  
 [方法: リソース ファイルを使用して、ローカライズされた名前、プロパティ、およびアクセス許可](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [方法: SharePoint プロジェクトに既存の BDC モデル ファイルを追加](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [方法: BDC モデルを作成](../sharepoint/how-to-create-a-bdc-model.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  