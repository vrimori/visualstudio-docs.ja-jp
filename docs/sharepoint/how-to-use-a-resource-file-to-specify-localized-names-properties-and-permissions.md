---
title: "方法: リソース ファイルを使用して、ローカライズした名前、プロパティ、およびアクセス許可を指定する | Microsoft Docs"
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
  - "BDC [Visual Studio での SharePoint 開発], ローカライズ (文字列を)"
  - "BDC [Visual Studio での SharePoint 開発], プロパティ"
  - "BDC [Visual Studio での SharePoint 開発], リソース ファイル"
  - "BDC [Visual Studio での SharePoint 開発], リソース文字列"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], ローカライズ (文字列を)"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], プロパティ"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], リソース ファイル"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], リソース文字列"
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 方法: リソース ファイルを使用して、ローカライズした名前、プロパティ、およびアクセス許可を指定する
  リソース ファイルを使用して、ローカライズされた名前を指定し、プロパティを定義し、Business Data Connectivity \(BDC\) モデルで定義されているアクセス許可の岩山オブジェクトを適用できます。  この情報を指定するには、**\[ビジネス データ接続モデル\]** 項目を含むプロジェクトに **\[ビジネス データ接続リソース項目\]** 項目を追加します。  次に、リソース ファイルの XML を編集して、名前、プロパティ、およびアクセス許可を指定します。  
  
### SharePoint プロジェクトに BDC リソース ファイルを追加するには  
  
1.  **\[ソリューション エクスプローラー\]** で、SharePoint プロジェクトのフォルダーを展開し、BDC モデルを含むフォルダーを選択します。  
  
2.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
3.  **\[SharePoint\]** ノードを展開し、**2010** ノードを選択します。  
  
4.  **\[新しいアイテムの追加\]** ダイアログ ボックスで、**\[ビジネス データ接続リソース項目\]** をクリックします。  
  
5.  **\[名前\]** ボックスで、リソース ファイルの名前を指定し、**\[追加\]** ボタンをクリックします。  
  
     拡張子が .bdcr のリソース ファイルがプロジェクトに追加され、編集用に開きます。  
  
6.  BDC モデルに適用するローカライズされた名前、プロパティ、およびアクセス許可を定義する XML を追加します。  
  
     これらの要素を定義する方法の詳細については、"参照してください [モデルとリソース ファイル](http://go.microsoft.com/fwlink/?LinkID=169283)。  
  
## 参照  
 [方法: 既存の BDC モデル ファイルを SharePoint プロジェクトに追加する](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [方法: BDC モデルを作成する](../sharepoint/how-to-create-a-bdc-model.md)   
 [方法: BDC 機能にカスタム アセンブリを含める](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  