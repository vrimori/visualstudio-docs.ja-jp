---
title: "BDC モデルのデザイン ツールの概要"
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
  - "VS.SharePointTools.BDC.Method_Details"
  - "VS.SharePointTools.BDC.Explorer"
  - "VS.SharePointTools.BDC.Diagram"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [Visual Studio での SharePoint 開発], BDC エクスプローラー"
  - "BDC [Visual Studio での SharePoint 開発], デザイナー"
  - "BDC [Visual Studio での SharePoint 開発], メソッドの詳細"
  - "BDC [Visual Studio での SharePoint 開発], ビジュアル ツール"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], BDC エクスプローラー"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], デザイナー"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], メソッドの詳細"
  - "ビジネス データ接続サービス [Visual Studio での SharePoint 開発], ビジュアル ツール"
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# BDC モデルのデザイン ツールの概要
  BDC デザイナー、**\[BDC メソッドの詳細\]** ウィンドウ、および **BDC エクスプローラー**を使用して、ビジネス データ接続 \(BDC\) モデルをデザインできます。  
  
 **BDC エクスプローラー**を使用すると、モデルの参照、モデルの検索、および型記述子の定義を行うことができます。  
  
## BDC デザイナー  
 BDC デザイナーを使用すると、モデル内のエンティティを定義し、相互の関係性を視覚的に整理することができます。  BDC デザイナーは、次のタスクを実行するときに使用します。  
  
-   モデルにエンティティを追加する。  
  
-   モデルからエンティティを削除する。  
  
-   エンティティ間の関連性を定義する。  
  
 BDC デザイナーを開き、プロジェクトのモデル ファイルをダブルクリックするか、またはモデル ファイルのショートカット メニューを開き、**\[開く\]** をクリックします。  デザイナーに **\[ツールボックス\]** から **\[エンティティ\]** をドラッグするか、またはコピーすることで、モデルにエンティティを追加します。  2 個のエンティティ間に関連付けを作成するには、**\[ツールボックス\]** の **\[関連付け\]** のコントロールを選択し、最初のエンティティを選択し、2 番目のエンティティを選択します。  
  
## \[BDC メソッドの詳細\] ウィンドウ  
 **\[BDC メソッドの詳細\]** ウィンドウを使用して、メソッドのパラメーター、インスタンス、およびフィルターの記述子を定義します。  
  
 **\[BDC メソッドの詳細\]** ウィンドウを使用すると、Finder、SpecificFinder、Creator、Updater、および Deleter の各メソッドを簡単に生成できます。  これらのメソッドを生成すると、パラメーター、インスタンス、型記述子などのメタデータがメソッドに追加されます。  独自のシナリオに合わせて、このメタデータを変更することもできます。  
  
 **\[BDC メソッドの詳細\]** ウィンドウのメニュー バーで開くには、**\[その他のウィンドウ\]**、**\[BDC メソッドの詳細\]\[表示\]** をクリックします。  
  
 **\[BDC メソッドの詳細\]** ウィンドウのメソッドを表示するには、BDC デザイナーでエンティティを選択します。  選択したエンティティのメソッドが **\[BDC メソッドの詳細\]** ウィンドウに表示されます。  BDC デザイナーでエンティティを選択すると、**\[BDC メソッドの詳細\]** ウィンドウに情報が表示されません。  
  
 **\[BDC メソッドの詳細\]** ウィンドウのノードを展開したり折りたたんだりして、パラメーター、インスタンス、およびフィルターの記述子を定義します。  **BDC エクスプローラー**を使用して型記述子を定義します。  
  
## BDC エクスプローラー  
 **BDC エクスプローラー**には、モデルを構成する要素が表示されます。  **\[BDC エクスプローラー\]** のメニュー バーで開くには、**\[その他のウィンドウ\]**、**\[BDC エクスプローラー\]\[表示\]** をクリックします。  モデルを参照するには、**BDC エクスプローラー**のノードを展開します。  各ノードは、モデル ファイルの XML に含まれる 1 つの要素を表します。  
  
 **\[BDC エクスプローラー\]** のノードを選択すると、選択した各ノードの **\[プロパティ\]** はプロパティ ウィンドウに表示されます。  このようなプロパティの多くは、モデル ファイルの属性に対応しています。  **BDC エクスプローラー**の上部にある検索ボックスを使用して、モデルを検索することもできます。  
  
> [!NOTE]  
>  **BDC エクスプローラー**には、識別子、カスタム プロパティ、ローカライズした文字列、関連付けグループ、操作、フィルター記述子、アクション制御リスト、および既定のパラメーターの値が表示されません。  
  
### 型記述子の定義  
 **BDC エクスプローラー**を使用して型記述子を定義します。  BDC エクスプローラーを使用すると、1 回で型記述子を定義し、モデルの他の場所でその型記述子を再利用できるようになります。  この場合、型記述子をコピーし、他のパラメーターまたは型記述子に貼り付けます。  
  
> [!NOTE]  
>  元の型記述子が変更されても、型記述子のコピーに影響はありません。  
  
 詳細については、「[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)」を参照してください。  
  
## 参照  
 [方法: BDC モデルを作成する](../sharepoint/how-to-create-a-bdc-model.md)   
 [方法: モデルにエンティティを追加する](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [方法: Finder メソッドを追加する](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: SpecificFinder メソッドを追加する](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加する](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Deleter メソッドを追加する](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドを追加する](../sharepoint/how-to-add-an-updater-method.md)   
 [エンティティ間の関連付けの作成](../sharepoint/creating-an-association-between-entities.md)   
 [チュートリアル: ビジネス データを使用した SharePoint での外部リストの作成](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [SharePoint へのビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  