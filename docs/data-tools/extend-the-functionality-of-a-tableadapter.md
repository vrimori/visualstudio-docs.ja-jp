---
title: TableAdapter の機能を拡張します。
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9b5884ff140097010c90fbf2208fecd95980f2fe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>TableAdapter の機能を拡張します。
TableAdapter の機能を拡張するには、TableAdapter の部分クラス ファイルにコードを追加します。

 TableAdapter での変更が行われるときに TableAdapter を定義するコードが再生成、**データセット デザイナー**、か、ウィザードが、TableAdapter の構成を変更するときにします。 コードが、TableAdapter の再生時に削除されないようにするには、TableAdapter の部分クラス ファイルにコードを追加します。

 部分クラスを複数の物理ファイルに分割する特定のクラスのコードを許可します。 詳細については、次を参照してください。[部分](/dotnet/visual-basic/language-reference/modifiers/partial)または[partial (型)](/dotnet/csharp/language-reference/keywords/partial-type)です。

## <a name="locate-tableadapters-in-code"></a>コード内で Tableadapter を検索します。
 Tableadapter がでデザインされます、**データセット デザイナー**、生成された TableAdapter クラスがの入れ子になったクラスではない<xref:System.Data.DataSet>です。 Tableadapter は、TableAdapter の関連付けられているデータセットの名前に基づいて、名前空間にあります。 たとえば、アプリケーションには、という名前のデータセットが含まれています。 `HRDataSet`、に Tableadapter を配置すると、`HRDataSetTableAdapters`名前空間。 (このパターンに従っている名前付け規則: *DatasetName* + `TableAdapters`)。

 次の例では、という名前の TableAdapter`CustomersTableAdapter`を使用したプロジェクトでは、`NorthwindDataSet`です。

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>TableAdapter の部分クラスを作成するには

1.  移動して、プロジェクトに新しいクラスを追加、**プロジェクト**メニューを選択して**クラスの追加**です。

2.  クラスに `CustomersTableAdapterExtended` という名前を付けます。

3.  選択**追加**です。

4.  次のように正しい名前空間とプロジェクトの名前を部分クラスにコードを置き換えます。

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>関連項目

- [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)