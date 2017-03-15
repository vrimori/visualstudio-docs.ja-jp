---
title: "方法 : 型指定されたデータセットを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データセット [Visual Basic], 作成"
  - "型指定されたデータセット, 作成"
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 36
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : 型指定されたデータセットを作成する
**データ ソース構成**ウィザードまたは[型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)を使用して、型指定された <xref:System.Data.DataSet> を作成します。  
  
> [!NOTE]
>  プログラムでデータセットを作成する方法については、「[DataSet の作成](../Topic/Creating%20a%20DataSet.md)」を参照してください。  
  
## データ ソース構成ウィザードまたはデータセット デザイナーを使った型指定されたデータセットの作成  
  
#### データ ソース構成ウィザードでデータセットを作成するには  
  
1.  **\[データ\]** メニューの **\[新しいデータ ソースの追加\]** をクリックして**データ ソース構成**ウィザードを起動します。  
  
2.  **\[データソースの種類を選択\]** ページで、**\[データベース\]** をクリックします。  
  
3.  ウィザードを完了すると、型指定されたデータセットがプロジェクトに追加されます。  詳細については、「[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)」を参照してください。  
  
#### データセット デザイナーでデータセットを作成するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスの **\[データセット\]** を選択します。  
  
3.  データセットの名前を入力します。  
  
4.  **\[追加\]** をクリックします。  
  
     データセットがプロジェクトに追加され、**データセット デザイナー**にデータセットが開きます。  
  
5.  **ツールボックス**の **\[データセット\]** タブからデザイナーに項目をドラッグします。  詳細については、「[方法 : データセットを編集する](../Topic/How%20to:%20Edit%20a%20Dataset.md)」を参照してください。  
  
     または  
  
     **サーバー エクスプローラー**または**データベース エクスプローラー**のアクティブな接続から項目を**データセット デザイナー**にドラッグします。  
  
## 参照  
 [チュートリアル: データベース内のデータへの接続 \(Windows フォーム\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [方法 : データセットを編集する](../Topic/How%20to:%20Edit%20a%20Dataset.md)   
 [TableAdapter](../Topic/TableAdapters.md)   
 [データセットのリレーションシップ](../data-tools/relationships-in-datasets.md)   
 [Visual Studio でのデータセットの操作](../data-tools/dataset-tools-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)