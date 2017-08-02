---
title: "方法: BDC 機能にカスタム アセンブリを含める"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Add_Assemblies_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio での SharePoint 開発], 追加 (参照を)"
  - "BDC [Visual Studio での SharePoint 開発], カスタム アセンブリ"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 追加 (参照を)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], カスタム アセンブリ"
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 方法: BDC 機能にカスタム アセンブリを含める
  プロジェクトから、同じソリューションに含まれる他のプロジェクトのアセンブリを参照できます。  ただし、**\[参照アセンブリの LobSystems への割り当て\]** ダイアログ ボックスを使用して、プロジェクトのフィーチャー ファイルにこれらのアセンブリを追加する必要があります。  
  
### ビジネス データ接続機能にカスタム アセンブリを含めるには  
  
1.  **\[ソリューション エクスプローラー\]** で、BDC モデルを含むフォルダーを選択します。  
  
2.  **\[表示\]** メニューの **\[プロパティ ウィンドウ\]** をクリックします。  
  
3.  次に **\[プロパティ\]** ウィンドウで、**\[アセンブリ\]** とプロパティの省略記号ボタン\(...\)を選択します \(![ASP.NET モバイル デザイナー楕円](~/docs/sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")\)。  
  
     **\[参照アセンブリの LobSystems への割り当て\]** ダイアログ ボックスが表示されます。  
  
4.  **\[アセンブリの選択\]** の一覧で、カスタム アセンブリを選択します。  
  
    > [!NOTE]  
    >  アセンブリを含むプロジェクトへの参照を追加した場合、**\[参照アセンブリの LobSystems への割り当て\]** ダイアログ ボックスにはアセンブリのみが表示されます。  詳細については、「[方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)」を参照してください。  
  
5.  **\[参照プロパティ\]** グループでは、**\[LobSystem スコープ\]** のプロパティに表示されるリストを選択し、カスタム アセンブリを使用するを選択して、次へを **\[OK\]** ボタンを開きます。メソッドの LOB システムを。  
  
    > [!NOTE]  
    >  カスタム アセンブリのコードをデバッグするには、アセンブリをソリューション パッケージに追加する必要があります。  詳細については、「[方法: アセンブリを追加および削除する](../sharepoint/how-to-add-and-remove-additional-assemblies.md)」を参照してください。  
  
## 参照  
 [方法: リソース ファイルを使用して、ローカライズした名前、プロパティ、およびアクセス許可を指定する](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [方法: 既存の BDC モデル ファイルを SharePoint プロジェクトに追加する](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [方法: BDC モデルを作成する](../sharepoint/how-to-create-a-bdc-model.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  