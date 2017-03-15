---
title: "方法 : データセットと TableAdapters を別々のプロジェクトに分離する | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "n 層アプリケーション, 分離 (データセットと TableAdapters を)"
  - "TableAdapter, n 層アプリケーション"
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : データセットと TableAdapters を別々のプロジェクトに分離する
[TableAdapter](../Topic/TableAdapters.md) およびデータセット クラスを別々のプロジェクトに生成できるように、型指定されたデータセットが強化されました。  これにより、アプリケーション層を分離して、n 層データ アプリケーションをすばやく生成できるようになります。  
  
 次の手順では、[型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)を使用して、生成された `TableAdapter` コードを含むプロジェクトとは別個のプロジェクトにデータセット コードを生成するプロセスについて説明します。  
  
## データセットと TableAdapters の分離  
 `TableAdapter` コードからデータセット コードを分離する場合、データセット コードを含めるプロジェクトを現在のソリューションに配置する必要があります。  このプロジェクトが現在のソリューションに配置されていない場合、**\[プロパティ\]** ウィンドウの **\[DataSet プロジェクト\]** の一覧で使用できなくなります。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### データセットを別のプロジェクトに分離するには  
  
1.  データセット \(.xsd ファイル\) を含むソリューションを開きます。  
  
    > [!NOTE]
    >  データセット コードの分離先のプロジェクトがソリューションに含まれていない場合は、プロジェクトを作成するか、既存のプロジェクトをソリューションに追加します。  
  
2.  **ソリューション エクスプローラー**で型指定されたデータセット ファイル \(.xsd ファイル\) をダブルクリックして、**データセット デザイナー**でデータセットを開きます。  
  
3.  **データセット デザイナー**の空の領域をクリックします。  
  
4.  **\[プロパティ\]** ウィンドウで、**\[DataSet プロジェクト\]** ノードを見つけます。  
  
5.  **\[DataSet プロジェクト\]** の一覧で、データセット コードを生成するプロジェクトの名前をクリックします。  
  
     データセット コードを生成するプロジェクトをクリックすると、**"DataSet ファイル"** プロパティに既定のファイル名が設定されます。  必要な場合はこの名前を変更できます。  さらに、データセット コードを特定のディレクトリに生成する場合は、**"プロジェクト フォルダー"** プロパティをフォルダーの名前に設定できます。  
  
    > [!NOTE]
    >  **"DataSet プロジェクト"** プロパティを設定してデータセットと TableAdapter を分離する場合でも、プロジェクト内の既存のデータセット部分クラスは自動的には移動されません。  既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。  
  
6.  データセットを保存します。  
  
     データセット コードが、**\[DataSet プロジェクト\]** プロパティで選択したプロジェクトに生成され、**TableAdapter** コードが現在のプロジェクトに生成されます。  
  
 既定では、データセットと `TableAdapter` コードを分離すると、結果としてプロジェクトごとに別個のクラス ファイルが生成されます。  元のプロジェクトには、`TableAdapter` コードを含む DatasetName.Designer.vb \(または DatasetName.Designer.cs\) というファイルが存在します。  **"DataSet プロジェクト"** プロパティで指定したプロジェクトには、データセット コードを含む DatasetName.DataSet.Designer.vb \(または DatasetName.DataSet.Designer.cs\) というファイルが存在します。  
  
> [!NOTE]
>  データセットまたは `TableAdapter` プロジェクトを選択し、**ソリューション エクスプローラー**で **\[すべてのファイルを表示\]** をクリックして生成されたクラス ファイルを表示します。  
  
## 参照  
 [n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)   
 [チュートリアル : n 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [階層更新](../data-tools/hierarchical-update.md)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](../Topic/ADO.NET.md)