---
title: n 層アプリケーションでのデータセットの操作
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: d89c3a5582ef1c84c455801d3766d65246e34dea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899640"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>n 層アプリケーションでのデータセットの操作

*n 層データ アプリケーション*とは、複数の論理レイヤー (つまり*層*) に分離されるデータ中心のアプリケーションです。 言い換えれば、n 層データ アプリケーションは、複数のプロジェクトに分離されたアプリケーションであり、データ アクセス層、ビジネス ロジック層、およびプレゼンテーション層がそれぞれ独自のプロジェクトに含まれています。 詳細については、次を参照してください。 [N 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)します。

TableAdapter およびデータセット クラスを別々のプロジェクトに生成できるように、型指定されたデータセットが強化されました。 これにより、アプリケーション層を分離して、n 層データ アプリケーションをすばやく生成できます。

型指定されたデータセットで N 層サポートには、アプリケーションのアーキテクチャを n 層デザインに反復開発ができます。また、手動でコードを 1 つ以上のプロジェクトに分離するための要件も削除されます。 使用して、データ層のデザイン、**データセット デザイナー**します。 アプリケーション アーキテクチャを n 層デザインにする準備ができたら、データセット クラスが別個のプロジェクトに生成されるようにデータセットの **[DataSet プロジェクト]** プロパティを設定します。

## <a name="reference"></a>参照

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>関連項目

- [n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)
- [チュートリアル: n 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [n 層アプリケーションの TableAdapters にコードを追加する](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [n 層アプリケーションのデータセットにコードを追加する](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [n 層データセットに検証を追加する](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [データセットと TableAdapters を別々のプロジェクトに分離する](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [階層更新](../data-tools/hierarchical-update.md)
- [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)
- [Tableadapter の作成および構成](../data-tools/create-and-configure-tableadapters.md)
- [LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)