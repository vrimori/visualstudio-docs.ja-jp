---
title: "N 層アプリケーションのデータセットにコードを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 26dd5500f50b185c31809d9882e03e56541a567a
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>N 層アプリケーションのデータセットにコードを追加します。
データセットの部分クラス ファイルを作成し、コードを追加して、データセットの機能を拡張することができます (コードを追加するのではなく、 *DatasetName*です。Dataset.Designer ファイル) です。 部分クラスでは、コードを複数の物理ファイルに分割する特定のクラスを有効にします。 詳細については、次を参照してください。[部分](/dotnet/visual-basic/language-reference/modifiers/partial)または[部分クラスとメソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)です。  
  
(型指定されたデータセット) のデータセット定義を変更するたびに、データセットを定義するコードが生成されます。 データセットの構成を変更するウィザードの実行中に変更を加えると、このコードは生成されます。 コードが、データセットの再生時に削除されないようにするには、データセットの部分クラス ファイルにコードを追加します。  
  
既定では、データセットと TableAdapter のコードを分離する、結果は、プロジェクトごとに別個のクラス ファイルです。 元のプロジェクトがという名前のファイル*DatasetName*です。(または*DatasetName*です。Designer.cs) TableAdapter のコードを含むです。 指定されているプロジェクト、 **Dataset プロジェクト**プロパティという名前のファイルは、 *DatasetName*です。DataSet.Designer.vb (または*DatasetName*です。DataSet.Designer.cs)。このファイルには、データセット コードが含まれています。  
  
> [!NOTE]
>  データセットと Tableadapter を分離する場合 (設定して、 **DataSet プロジェクト**プロパティ)、プロジェクト内の既存のデータセット部分クラスを自動的に移動されません。 既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。  
  
> [!NOTE]
>  検証コードを追加する必要があると、型指定されたデータセットが生成するための機能を提供<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.RowChanging>イベント ハンドラー。 詳細については、次を参照してください。 [n 層データセットに検証を追加](../data-tools/add-validation-to-an-n-tier-dataset.md)です。  
  
## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>N 層アプリケーションのデータセットにコードを追加するには  
  
1.  .Xsd ファイルを含むプロジェクトを見つけます。 
  
2.  選択、 **.xsd**ファイルを開くには、データセットです。  
  
3.  コード (タイトル バーにテーブル名) を追加し、選択するデータ テーブルを右クリックして**コードの表示**です。  
  
     部分クラスが作成され、コード エディターで開きます。  
  
4.  部分クラス宣言内のコードを追加します。  
  
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
[N 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)   
[n 層アプリケーションの TableAdapters にコードを追加する](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[作成し、Tableadapter を構成します。](create-and-configure-tableadapters.md)  
[階層更新の概要](hierarchical-update.md)     
[Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)