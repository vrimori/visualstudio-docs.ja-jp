---
title: "n 層アプリケーションでのデータセットの操作 | Microsoft Docs"
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
  - "データ [Visual Basic], n 層アプリケーション"
  - "DataSet プロジェクト [VS n 層アプリケーション]"
  - "データセット [Visual Basic], n 層アプリケーション"
  - "分散アプリケーション [VS n 層アプリケーション]"
  - "複数層アプリケーション"
  - "多階層データベース アプリケーション"
  - "n 層アプリケーション"
  - "TableAdapter, n 層アプリケーション"
  - "層, n 層アプリケーション"
  - "型指定されたデータセット, n 層アプリケーション"
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# n 層アプリケーションでのデータセットの操作
*n 層データ アプリケーション*とは、複数の論理レイヤー \(つまり*層*\) に分離されるデータ中心のアプリケーションです。  言い換えれば、n 層データ アプリケーションは、複数のプロジェクトに分離されたアプリケーションであり、データ アクセス層、ビジネス ロジック層、およびプレゼンテーション層がそれぞれ独自のプロジェクトに含まれています。  詳細については、「[n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)」を参照してください。  
  
 TableAdapter およびデータセット クラスを別々のプロジェクトに生成できるように、型指定されたデータセットが強化されました。  これにより、アプリケーション層を分離して、n 層データ アプリケーションをすばやく生成できます。  
  
 型指定されたデータセットで n 層をサポートすることにより、アプリケーション アーキテクチャを n 層デザインに反復開発することが可能になり、コードを複数のプロジェクトに手動で分離する必要がなくなります。  データ層のデザインは、[型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)を使用して開始します。  アプリケーション アーキテクチャを n 層デザインにする準備ができたら、データセット クラスが別個のプロジェクトに生成されるようにデータセットの **\[DataSet プロジェクト\]** プロパティを設定します。  
  
## このセクションの内容  
 [方法 : データセットと TableAdapters を別々のプロジェクトに分離する](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 生成されたデータセット クラスを、生成された TableAdapter クラスを含むプロジェクトから新しいプロジェクトに移動する方法について説明します。  
  
 [方法 : n 層アプリケーションの TableAdapters にコードを追加する](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 n 層 TableAdapter のコードを追加できる部分クラスを生成する方法について説明します。  
  
 [方法 : n 層アプリケーションのデータセットにコードを追加する](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 n 層データセットのコードを追加できる部分クラスを生成する方法について説明します。  
  
 [方法 : n 層データセットに検証を追加する](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 データの変更時に検証を実行するコードを追加する場所について説明します。  
  
 [チュートリアル : n 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 型指定されたデータセットを作成し、TableAdapter とデータセット コードを複数のプロジェクトに分離する手順について説明します。  
  
 [チュートリアル : n 層データ アプリケーションへの検証の追加](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)  
 n 層データ アプリケーションのチュートリアルで作成したアプリケーションに検証を追加する手順について説明します。  
  
## 関連項目  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## 関連項目  
 [n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)  
  
 [階層更新](../data-tools/hierarchical-update.md)  
  
 [Visual Studio でのデータセットの操作](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)  
  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)  
  
 [N\-Tier and Remote Applications with LINQ to SQL](../Topic/N-Tier%20and%20Remote%20Applications%20with%20LINQ%20to%20SQL.md)