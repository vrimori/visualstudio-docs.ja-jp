---
title: n 層アプリケーションの TableAdapters にコードを追加する
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e5a9aad4aaecb629f5860fadf56e35a55455be63
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38783091"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>n 層アプリケーションの TableAdapters にコードを追加する
TableAdapter の部分クラス ファイルを作成し、コードを追加して、TableAdapter の機能を拡張することができます (コードを追加するのではなく、 *DatasetName.DataSet.Designer*ファイル)。 部分クラスには、特定のクラスを複数の物理ファイルに分割するためのコードが有効にします。 詳細については、次を参照してください。[部分](/dotnet/visual-basic/language-reference/modifiers/partial)または[partial (型)](/dotnet/csharp/language-reference/keywords/partial-type)します。

データセットに TableAdapter を変更するたびに、TableAdapter を定義するコードが生成されます。 このコードは、TableAdapter の構成を変更するウィザードの実行中に変更されたときにも生成されます。 コードが、TableAdapter の再生成中に削除されないようにするには、TableAdapter の部分クラス ファイルにコードを追加します。

既定では、データセットと TableAdapter コードを分離したら、結果はプロジェクトごとに別個のクラス ファイルが。 元のプロジェクトにという名前のファイル*DatasetName.Designer.vb* (または*DatasetName.Designer.cs*) TableAdapter コードを格納しています。 指定されているプロジェクト、 **Dataset プロジェクト**プロパティという名前のファイルは、 *DatasetName.DataSet.Designer.vb* (または*DatasetName.DataSet.Designer.cs*) します。データセット コードが含まれています。

> [!NOTE]
>  データセットと Tableadapter を分離する場合 (設定して、 **DataSet プロジェクト**プロパティ)、プロジェクト内の既存のデータセット部分クラスが自動的に移動されません。 既存のデータセット部分クラスは、データセット プロジェクトに手動で移動する必要があります。

> [!NOTE]
> データセットを生成するための機能を提供する<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.RowChanging>検証が必要なときにイベント ハンドラー。 詳細については、次を参照してください。 [n 層データセットに検証を追加](../data-tools/add-validation-to-an-n-tier-dataset.md)します。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>N 層アプリケーションでの TableAdapter にユーザー コードを追加するには

1.  含むプロジェクトを見つけ、 *.xsd*ファイル。

2.  ダブルクリックして、 *.xsd*ファイルを開く、**データセット デザイナー**します。

3.  コードを追加し、選択する TableAdapter を右クリックして**コードの表示**します。

     部分クラスが作成され、コード エディターで開きます。

4.  部分クラス宣言内でコードを追加します。

5.  次の例では、コードを追加する場所、`CustomersTableAdapter`で、 `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>関連項目

- [N 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)
- [n 層アプリケーションのデータセットにコードを追加する](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Tableadapter の作成および構成](create-and-configure-tableadapters.md)
- [階層更新の概要](hierarchical-update.md)
