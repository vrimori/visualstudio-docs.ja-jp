---
title: N 層アプリケーションの TableAdapters にコードを追加 |Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd46596ff474a33be42b8c5118404845a39c2b7d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538689"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>n 層アプリケーションの TableAdapters にコードを追加する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[n 層アプリケーションの TableAdapters にコードを追加](https://docs.microsoft.com/visualstudio/data-tools/add-code-to-tableadapters-in-n-tier-applications)します。  
  
  
機能を拡張することができます、`TableAdapter`の部分クラス ファイルを作成して、`TableAdapter`コードを追加し、(コードを追加するのではなく、 *DatasetName*します。DataSet.Designer ファイル)。 部分クラスには、特定のクラスを複数の物理ファイルに分割するためのコードが有効にします。 詳細については、次を参照してください。[部分](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)または[partial (型)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)します。  
  
 定義するコードを`TableAdapter`は変更されるたびに生成される、 `TableAdapter` (で、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md))。 構成を変更するウィザードの実行中に変更されたときに、このコードは生成も、`TableAdapter`します。 コードが再生成中に削除されないようにする、 `TableAdapter`、コードの部分クラス ファイルを追加、`TableAdapter`します。  
  
 既定では、データセットと `TableAdapter` コードを分離すると、結果としてプロジェクトごとに別個のクラス ファイルが生成されます。 元のプロジェクトにという名前のファイル*DatasetName*します。(または*DatasetName*します。Designer.cs) を含む、`TableAdapter`コード。 指定されているプロジェクト、 **Dataset プロジェクト**プロパティという名前のファイルは、 *DatasetName*します。DataSet.Designer.vb (または*DatasetName*します。DataSet.Designer.cs) データセット コードを格納しています。  
  
> [!NOTE]
>  データセットを分離する場合と`TableAdapter`s (設定して、 **DataSet プロジェクト**プロパティ)、プロジェクト内の既存のデータセット部分クラスが自動的に移動されません。 既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。  
  
> [!NOTE]
>  [の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)を生成するための機能を提供<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.RowChanging>検証が必要なときにイベント ハンドラー。 詳細については、次を参照してください。 [n 層データセットに検証を追加](../data-tools/add-validation-to-an-n-tier-dataset.md)します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>N 層アプリケーションでの TableAdapter にユーザー コードを追加するには  
  
1.  .Xsd ファイルを含むプロジェクトが見つかりません (、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md))。  
  
2.  ダブルクリックして、 **.xsd**ファイルを開く、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)します。  
  
3.  右クリックし、 `TableAdapter` 、コードを追加し、選択する**コードの表示**します。  
  
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
 [N 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)   
 [N 層アプリケーションでのデータセットにコードを追加します。](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [Tableadapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [TableAdapterManager の概要](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [階層更新の概要](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [データ アプリケーションの作成](../data-tools/creating-data-applications.md)

