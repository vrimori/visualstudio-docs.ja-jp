---
title: n 層アプリケーションのデータセットにコードを追加する
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c2d1784e498cb856cc388b8e7f26dd57f978e79f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927390"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>n 層アプリケーションのデータセットにコードを追加する
データセットの機能を拡張するには、データセットの部分クラス ファイルを作成し、コードを追加 (コードを追加するのではなく、 *DatasetName*します。Dataset.Designer ファイル)。 部分クラスには、特定のクラスを複数の物理ファイルに分割するためのコードが有効にします。 詳細については、次を参照してください。[部分](/dotnet/visual-basic/language-reference/modifiers/partial)または[部分クラスとメソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)します。

(型指定されたデータセット) のデータセット定義を変更するたびに、データセットを定義するコードが生成されます。 このコードは、データセットの構成を変更するウィザードの実行中に変更するときにも生成されます。 コードが、データセットの再生成中に削除されないようにするには、データセットの部分クラス ファイルにコードを追加します。

既定では、データセットと TableAdapter コードを分離したら、結果はプロジェクトごとに別個のクラス ファイルが。 元のプロジェクトにという名前のファイル*DatasetName.Designer.vb* (または*DatasetName.Designer.cs*) TableAdapter コードを格納しています。 指定されているプロジェクト、 **Dataset プロジェクト**プロパティという名前のファイルは、 *DatasetName.DataSet.Designer.vb* (または*DatasetName.DataSet.Designer.cs*).このファイルには、データセット コードが含まれています。

> [!NOTE]
>  データセットと Tableadapter を分離する場合 (設定して、 **DataSet プロジェクト**プロパティ)、プロジェクト内の既存のデータセット部分クラスが自動的に移動しません。 既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。

> [!NOTE]
>  検証コードを追加する必要があると、に型指定されたデータセットが生成するための機能を提供します<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.RowChanging>イベント ハンドラー。 詳細については、次を参照してください。 [n 層データセットに検証を追加](../data-tools/add-validation-to-an-n-tier-dataset.md)します。

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>N 層アプリケーションのデータセットにコードを追加するには

1.  含むプロジェクトを見つけ、 *.xsd*ファイル。

2.  選択、 **.xsd**ファイル データセットを開きます。

3.  コード (タイトル バーのテーブル名) を追加し、選択するデータ テーブルを右クリックして**コードの表示**します。

     部分クラスが作成され、コード エディターで開きます。

4.  部分クラス宣言内でコードを追加します。

     次の例は、NorthwindDataSet 内 CustomersDataTable にコードを追加する場所を示しています。

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```
    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>関連項目

- [n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)
- [n 層アプリケーションの TableAdapters にコードを追加する](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Tableadapter の作成および構成](create-and-configure-tableadapters.md)
- [階層更新の概要](hierarchical-update.md)
- [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)