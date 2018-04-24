---
title: 別のデータセットと TableAdapters を別々 のプロジェクトに
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 691ff9c46e951f32bf8652d83a218f6c1e121382
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>別のデータセットと TableAdapters を別々 のプロジェクトに
型指定されたデータセットが強化されたできるように、 [Tableadapter](create-and-configure-tableadapters.md)別々 のプロジェクトにデータセット クラスを生成することができます。 これにより、アプリケーション層を分離して、n 層データ アプリケーションをすばやく生成できるようになります。

次の手順を使用するプロセスの説明、**データセット デザイナー**は TableAdapter に生成されたコードを含むプロジェクトから別のプロジェクトにデータセット コードを生成します。

## <a name="separate-datasets-and-tableadapters"></a>別のデータセットと TableAdapters
TableAdapter のコードからデータセット コードを分離する場合は、データセット コードを含むプロジェクトを現在のソリューション内になければなりません。 このプロジェクトが現在のソリューションにない場合は、ことができなくの利用可能な**DataSet プロジェクト**一覧に、**プロパティ**ウィンドウです。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>データセットを別のプロジェクトに分離するには

1.  データセット (.xsd ファイル) を含むソリューションを開きます。

    > [!NOTE]
    >  ソリューションに、データセット コードを分離するプロジェクトが含まれていない場合、プロジェクトの作成または既存のプロジェクトをソリューションに追加します。

2.  型指定されたデータセット ファイル (.xsd ファイル) をダブルクリックして**ソリューション エクスプ ローラー**を開くには、データセットで、**データセット デザイナー**です。

3.  空の領域を選択して、**データセット デザイナー**です。

4.  **プロパティ**ウィンドウで、検索、 **DataSet プロジェクト**ノード。

5.  **DataSet プロジェクト**一覧で、データセット コードを生成するプロジェクトの名前を選択します。

     データセット コードを生成するプロジェクトを選択した後、**データセット ファイル**プロパティには、既定のファイル名が設定されます。 必要な場合は、この名前を変更できます。 さらに、特定のディレクトリに、データセット コードを生成する場合は、設定できます、**プロジェクト フォルダー**プロパティをフォルダーの名前にします。

    > [!NOTE]
    >  データセットと Tableadapter を分離する場合 (設定して、 **DataSet プロジェクト**プロパティ)、プロジェクト内の既存のデータセット部分クラスを自動的に移動されません。 既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。

6.  データセットを保存します。

     選択したプロジェクトに、データセット コードを生成、 **DataSet プロジェクト**プロパティ、および**TableAdapter**現在のプロジェクトにコードを生成します。

既定では、データセットと TableAdapter のコードを分離する、結果は、プロジェクトごとに別個のクラス ファイルです。 元のプロジェクト、ファイルが存在 TableAdapter のコードを含む DatasetName.Designer.vb (または DatasetName.Designer.cs) という名前です。 指定されているプロジェクト、 **Dataset プロジェクト**プロパティ ファイルには、データセット コードを含む DatasetName.DataSet.Designer.vb (または DatasetName.DataSet.Designer.cs) という名前です。

> [!NOTE]
>  生成されたクラス ファイルを表示するには、データセットまたは TableAdapter プロジェクトを選択します。 その後、**ソリューション エクスプ ローラー** **すべてのファイル**です。

## <a name="see-also"></a>関連項目

- [n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)
- [チュートリアル : n 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [階層更新](../data-tools/hierarchical-update.md)
- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)