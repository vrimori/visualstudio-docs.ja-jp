---
title: '方法: BDC 機能にカスタム アセンブリを含める |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3b53b7c8b5cf4dd2c13adbb53a9724a8adaf2328
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53919522"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>方法: BDC 機能にカスタム アセンブリを含める
  プロジェクトでは、同じソリューション内の他のプロジェクトからアセンブリを参照できます。 使用して、プロジェクトのフィーチャー ファイルにこれらのアセンブリを追加する必要があります、**参照されるアセンブリの LobSystems への割り当て** ダイアログ ボックス。  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>ビジネス データ接続 (BDC) 機能にカスタム アセンブリを含める
  
1.  **ソリューション エクスプ ローラー**、BDC モデルを含むフォルダーを選択します。  
  
2.  **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックします。  
  
3.  **プロパティ**ウィンドウで、選択、**アセンブリ**プロパティ、し、省略記号ボタン (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイルデザイナー楕円"))。  
  
     **参照されるアセンブリの LobSystems への割り当て** ダイアログ ボックスが表示されます。  
  
4.  **アセンブリを選択して**一覧で、カスタム アセンブリを選択します。  
  
    > [!NOTE]  
    >  アセンブリはのみに表示されます、**参照されるアセンブリの LobSystems への割り当て**ダイアログ ボックスで、アセンブリを含むプロジェクトへの参照を追加した場合。 詳細については、「[方法 :追加または参照の追加 ダイアログ ボックスを使用して参照を削除する](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)します。  
  
5.  **参照プロパティ**グループで、について表示される一覧を開き、 **LobSystem スコープ**プロパティ、LOB システムを選択し、カスタム アセンブリの使用方法の選択、 **[ok]** ボタンをクリックします。  
  
    > [!NOTE]  
    >  カスタム アセンブリ内のコードをデバッグするには、ソリューション パッケージに、アセンブリを追加する必要があります。 詳細については、「[方法 :追加およびその他のアセンブリを削除](../sharepoint/how-to-add-and-remove-additional-assemblies.md)します。  
  
## <a name="see-also"></a>関連項目
 [方法: リソース ファイルを使用して、ローカライズされた名前、プロパティ、およびアクセス許可を指定するには](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [方法: SharePoint プロジェクトに既存の BDC モデル ファイルを追加します。](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [方法: BDC モデルを作成します。](../sharepoint/how-to-create-a-bdc-model.md)   
 [SharePoint に Integragte ビジネス データ](../sharepoint/integrating-business-data-into-sharepoint.md)  
