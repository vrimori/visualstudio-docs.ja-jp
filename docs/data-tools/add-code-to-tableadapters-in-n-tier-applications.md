---
title: N 層アプリケーションの TableAdapters にコードを追加 |Microsoft ドキュメント
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 52c732842f5a98bfb1c78a125830f730aeeb5321
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>N 層アプリケーションの TableAdapters にコードを追加します。
TableAdapter の部分クラス ファイルを作成し、コードを追加して、TableAdapter の機能を拡張することができます (コードを追加するのではなく、 *DatasetName*です。DataSet.Designer ファイル) です。 部分クラスでは、コードを複数の物理ファイルに分割する特定のクラスを有効にします。 詳細については、次を参照してください。[部分](/dotnet/visual-basic/language-reference/modifiers/partial)または[partial (型)](/dotnet/csharp/language-reference/keywords/partial-type)です。  
  
データセットに TableAdapter を変更するたびに、TableAdapter を定義するコードが生成されます。 このコードは、TableAdapter の構成を変更するウィザードの実行中に変更が加えられても生成されます。 コードが、TableAdapter の再生時に削除されないようにするには、TableAdapter の部分クラス ファイルにコードを追加します。  
  
既定では、データセットと TableAdapter のコードを分離する、結果は、プロジェクトごとに別個のクラス ファイルです。 元のプロジェクトがという名前のファイル*DatasetName*です。(または*DatasetName*です。Designer.cs) TableAdapter のコードを含むです。 指定されているプロジェクト、 **Dataset プロジェクト**プロパティという名前のファイルは、 *DatasetName*です。DataSet.Designer.vb (または*DatasetName*です。DataSet.Designer.cs)、データセット コードを格納しています。  
  
> [!NOTE]
>  データセットと Tableadapter を分離する場合 (設定して、 **DataSet プロジェクト**プロパティ)、プロジェクト内の既存のデータセット部分クラスが自動的に移動されません。 既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。  
  
> [!NOTE]
>  データセットを生成するための機能を提供する<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.RowChanging>検証が必要なときにイベント ハンドラー。 詳細については、次を参照してください。 [n 層データセットに検証を追加](../data-tools/add-validation-to-an-n-tier-dataset.md)です。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>N 層アプリケーションの TableAdapter にユーザー コードを追加するには  
  
1.  .Xsd ファイルを含むプロジェクトを見つけます。
  
2.  ダブルクリックして、 **.xsd**ファイルを開くには、**データセット デザイナー**です。  
  
3.  コードを追加し、選択する TableAdapter を右クリックして**コードの表示**です。  
  
     部分クラスが作成され、コード エディターで開きます。  
  
4.  部分クラス宣言内のコードを追加します。  
  
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
[N 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)   
[N 層アプリケーションのデータセットにコードを追加します。](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
[作成し、Tableadapter を構成します。](create-and-configure-tableadapters.md)   
[階層更新の概要](hierarchical-update.md)   
