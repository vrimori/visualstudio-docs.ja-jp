---
title: "方法: 既存の BDC モデル ファイルを SharePoint プロジェクトに追加する | Microsoft Docs"
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
  - "VS.SharePointTools.BDC.ImportDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio での SharePoint 開発], インポート (モデルを)"
  - "BDC [Visual Studio での SharePoint 開発], 削除 (モデルを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], インポート (モデルを)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], 再利用 (モデルを)"
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 方法: 既存の BDC モデル ファイルを SharePoint プロジェクトに追加する
  SharePoint ファームのプロジェクトにモデル ファイル \(.bdcm\) を追加するには、Visual Studio を使用して Business Data Connectivity \(BDC\) モデルをカスタマイズし、パッケージ化、およびできます。  詳細については、「[ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)」を参照してください。  
  
### SharePoint プロジェクトに BDC モデル ファイルを追加するには、  
  
1.  **\[ソリューション エクスプローラー\]** で、SharePoint プロジェクトのフォルダーを選択します。  
  
2.  メニュー バーで **\[プロジェクト\]**、**\[既存項目の追加\]** の順に選択します。  
  
3.  **\[既存のアイテムを追加\]** ダイアログ ボックスで、プロジェクトに追加するモデル定義ファイルの場所にファイルを選択し、次へをクリックします **\[追加\]** ボタンを参照してください。  
  
     モデルで *.NET アセンブリ型の \(LOB\) 基幹業務 \(LOB\) システムを*定義する、**\[.NET アセンブリの LobSystem を追加\]** ダイアログ ボックスが表示されます。  
  
4.  ダイアログ ボックスが表示されたら、次の手順の実行: 1  
  
    -   カスタム コードを記述して、インポートしたモデルのメタデータを定義するためにデザイナーを使用する場合は、**\[はい\]** ボタンを選択し、システムを付けておくと、**\[OK\]** ボタンをクリックします。  
  
    -   それ以外の場合は **\[いいえ\]** をクリックし、**\[OK\]** ボタンをクリックします。  
  
     **ビジネス データ接続モデル項目**がプロジェクトに追加されます。  
  
## 参照  
 [ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [方法: BDC モデルを作成する](../sharepoint/how-to-create-a-bdc-model.md)   
 [方法: リソース ファイルを使用して、ローカライズした名前、プロパティ、およびアクセス許可を指定する](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [方法: BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  