---
title: N 層アプリケーションでデータセットの操作 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61f3686488a460ef4c7091521c2165f575e76fa6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544800"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>n 層アプリケーションでのデータセットの操作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[n 層アプリケーションでデータセットを操作](https://docs.microsoft.com/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)します。  
  
  
N 層データ アプリケーション * は複数の論理レイヤーに分離されるデータ中心のアプリケーション (または*層*)。 言い換えれば、n 層データ アプリケーションは、複数のプロジェクトに分離されたアプリケーションであり、データ アクセス層、ビジネス ロジック層、およびプレゼンテーション層がそれぞれ独自のプロジェクトに含まれています。 詳細については、次を参照してください。 [N 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)します。  
  
 TableAdapter およびデータセット クラスを別々のプロジェクトに生成できるように、型指定されたデータセットが強化されました。 これにより、アプリケーション層を分離して、n 層データ アプリケーションをすばやく生成できます。  
  
 型指定されたデータセットで N 層サポートには、アプリケーションのアーキテクチャを n 層デザインに反復開発ができます。また、手動でコードを 1 つ以上のプロジェクトに分離するための要件も削除されます。 使用して、データ層のデザイン、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)します。 N 層設計へのアプリケーション アーキテクチャを実行する準備ができたら、設定、 **DataSet プロジェクト**別のプロジェクトにデータセット クラスを生成するデータセットのプロパティ。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データセットと TableAdapters を別々のプロジェクトに分離する](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 生成されたデータセット クラスを、生成された TableAdapter クラスを含むプロジェクトから新しいプロジェクトに移動する方法について説明します。  
  
 [n 層アプリケーションの TableAdapters にコードを追加する](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 n 層 TableAdapter のコードを追加できる部分クラスを生成する方法について説明します。  
  
 [n 層アプリケーションのデータセットにコードを追加する](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 n 層データセットのコードを追加できる部分クラスを生成する方法について説明します。  
  
 [n 層データセットに検証を追加する](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 データの変更時に検証を実行するコードを追加する場所について説明します。  
  
 [チュートリアル : n 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 型指定されたデータセットを作成し、TableAdapter とデータセット コードを複数のプロジェクトに分離する手順について説明します。  
  
 [チュートリアル: N 層データ アプリケーションへの検証の追加](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 N 層データ アプリケーションのチュートリアルで作成されたアプリケーションに検証を追加する手順について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>関連項目  
 [n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)  
  
 [階層更新](../data-tools/hierarchical-update.md)  
  
 [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)  
  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)  
  
 [LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

