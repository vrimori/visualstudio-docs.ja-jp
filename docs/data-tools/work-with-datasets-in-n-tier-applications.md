---
title: "N 層アプリケーションでデータセットを操作 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 2274ac9bcfd3ba7c87364f5c4c79cd155844fe73
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="work-with-datasets-in-n-tier-applications"></a>N 層アプリケーションでのデータセットを操作します。
*N 層データ アプリケーション*は複数の論理レイヤーに分離されるデータ セントリックなアプリケーション (または*階層*)。 言い換えれば、n 層データ アプリケーションは、複数のプロジェクトに分離されたアプリケーションであり、データ アクセス層、ビジネス ロジック層、およびプレゼンテーション層がそれぞれ独自のプロジェクトに含まれています。 詳細については、次を参照してください。 [N 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)です。  
  
TableAdapter およびデータセット クラスを別々のプロジェクトに生成できるように、型指定されたデータセットが強化されました。 これにより、アプリケーション層を分離して、n 層データ アプリケーションをすばやく生成できます。  
  
型指定されたデータセットで N 層をサポートでは、アプリケーション アーキテクチャを n 層デザインに反復開発できるようにします。また、複数のプロジェクトにコードを手動で分離するための要件も削除されます。 使用して、データ層のデザイン、**データセット デザイナー**です。 アプリケーションのアーキテクチャを n 層デザインにする準備ができたら、設定、 **DataSet プロジェクト**を別のプロジェクトに、データセット クラスを生成するデータセットのプロパティです。  
  
## <a name="reference"></a>参照  
<xref:System.Data.DataSet>  
<xref:System.Data.TypedTableBase%601>  
  
## <a name="see-also"></a>関連項目
[n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)  
[チュートリアル : n 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
[n 層アプリケーションの TableAdapters にコードを追加する](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[n 層アプリケーションのデータセットにコードを追加する](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
[n 層データセットに検証を追加する](../data-tools/add-validation-to-an-n-tier-dataset.md)  
[データセットと TableAdapters を別々のプロジェクトに分離する](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
[階層更新](../data-tools/hierarchical-update.md)  
[Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)  
[Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)  
[作成し、Tableadapter を構成します。](../data-tools/create-and-configure-tableadapters.md)  
[LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)