---
title: TableAdapter の概要 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DataAccessor
- vbdata.Microsoft.VSDesigner.DataSource.DataAccessor
- TableAdapter
- vs.data.TableAdapter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], table adapters
- TableAdapters, queries
- data [Visual Studio], TableAdapters
- query data in Visual Studio
- TableAdapter.GetData
- TableAdapter.Fill
- data [Visual Studio], datasets
- TableAdapters
- table adapters
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fb5ebcdaa1bebe67c2fb8e378c7345467dd10b78
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269049"
---
# <a name="tableadapter-overview"></a>TableAdapter の概要
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tableadapter は、データベースへの接続、クエリまたはストアド プロシージャを実行し、返されたデータをデータ テーブルを入力するデザイナーで生成されるコンポーネントです。 TableAdapter は、更新されたデータをアプリケーションからデータベースに送り返す場合にも使用します。 TableAdapter が関連付けられているテーブルのスキーマに準拠するデータを返す限り、TableAdapter に好きなだけ多くのクエリがあることができます。 次の図は、Tableadapter がデータベースおよびメモリ内の他のオブジェクトとやり取りする方法を示しています。  
  
 ![クライアント アプリケーションでのデータ フロー](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Tableadapter は設計されています中に、**データセット デザイナー**の入れ子になったクラスとして生成された TableAdapter クラスは生成されません、<xref:System.Data.DataSet>します。 これらのクラスは、各データセットに固有の、個別の名前空間に格納されます。 たとえば、`NorthwindDataSet` という名前のデータセットがある場合、<xref:System.Data.DataTable> 内の `NorthwindDataSet` に関連付けられた TableAdapter は、`NorthwindDataSetTableAdapters` 名前空間に格納されます。 プログラムで特定の TableAdapter にアクセスするには、TableAdapter の新しいインスタンスを宣言する必要があります。 例えば:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>関連付けられた DataTable スキーマ  
 TableAdapter を作成する場合、最初のクエリまたはストアド プロシージャは、TableAdapter の関連 <xref:System.Data.DataTable> のスキーマを定義するために使用されます。 呼び出して、TableAdapter の最初のクエリまたはストアド プロシージャを実行する`Fill`メソッド (TableAdapter の値を格納する機能に関連付けられた<xref:System.Data.DataTable>)。 TableAdapter のメインのクエリに対する変更は、関連付けられたデータ テーブルのスキーマに反映されます。 たとえば、メインのクエリから列を削除すると、関連付けられたデータ テーブルから列が削除されます。 TableAdapter に関する他のクエリで、メインのクエリにない列の値を返す SQL ステートメントを使用する場合、デザイナーによって、メインのクエリとその他のクエリの間で、列の変更の同期が試みられます。 詳細については、次を参照してください。[方法: Tableadapter の編集](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)します。  
  
## <a name="tableadapter-update-commands"></a>TableAdapter 更新コマンド  
 TableAdapter の更新機能は、TableAdapter ウィザードで提供されるメインのクエリに基づく情報がどの程度存在するかによって異なります。 たとえば、複数のテーブル (JOIN)、スカラー値、ビュー、または集約関数の結果から値をフェッチするように設定された TableAdapter の場合、最初の作成時には、基になるデータベースに更新を戻す機能がありません。 ただし、手動で INSERT、UPDATE および DELETE コマンドを構成することができます、**プロパティ**ウィンドウ。  
  
## <a name="tableadapter-queries"></a>TableAdapter クエリ  
 ![複数のクエリによる TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Tableadapter には、複数のクエリ、関連するデータ テーブルの入力を含めることができます。 それぞれのクエリが、関連するデータ テーブルと同じスキーマに従ったデータを返す限り、アプリケーションに必要なクエリをいくつでも TableAdapter に定義できます。 これにより、多様な基準を満たすデータの読み込みが可能になります。 たとえば、アプリケーションに顧客のテーブルが含まれている場合、名前が特定の英字で始まるすべての顧客をこのテーブルに格納するクエリ、同じ州内のすべての顧客をこのテーブルに格納するクエリなどを作成できます。 特定の州内の顧客を `Customers` テーブルに格納するには、州の値を示すパラメーターを受け取る `FillByState` クエリを、`SELECT * FROM Customers WHERE State = @State` のように作成します。 このクエリは、`FillByState` メソッドを呼び出し、`CustomerTableAdapter.FillByState("WA")` のようにパラメーター値を渡して、実行します。 詳細については、次を参照してください。[方法: TableAdapter クエリの作成](../data-tools/how-to-create-tableadapter-queries.md)です。  
  
 TableAdapter のデータ テーブルと同じスキーマのデータを返すクエリの他に、スカラー (Single 型) 値を返すクエリを追加できます。 たとえば、顧客数を返すクエリ (`SELECT Count(*) From Customers`) は、返されるデータがテーブルのスキーマに準拠していなくても、`CustomersTableAdapter` に対しては有効です。  
  
## <a name="clearbeforefill-property"></a>ClearBeforeFill プロパティ  
 既定では、TableAdapter のデータ テーブルに値を格納するクエリを実行するたびに、データが消去され、クエリ結果だけがテーブルに読み込まれます。 クエリから返されたデータをデータ テーブル内の既存のデータに追加またはマージする場合は、TableAdapter の `ClearBeforeFill` プロパティを `false` に設定します。 データを消去するかどうかに関係なく、更新をデータベースに返すことが必要な場合は、明示的に送信する必要があります。 そのテーブルに値を格納する別のクエリを実行する前に、テーブル内のデータに加えた変更を保存してください。 詳細については、次を参照してください。 [TableAdapter を使用してデータ更新](../data-tools/update-data-by-using-a-tableadapter.md)します。  
  
## <a name="tableadapter-inheritance"></a>TableAdapter の継承  
 TableAdapter では、設定された <xref:System.Data.Common.DataAdapter> をカプセル化することにより、標準データ アダプターの機能が拡張されます。 既定では、TableAdapter は、<xref:System.ComponentModel.Component> から継承され、<xref:System.Data.Common.DataAdapter> クラスにキャストできません。 TableAdapter を <xref:System.Data.Common.DataAdapter> にキャストすると、<xref:System.InvalidCastException> が発生します。 派生したクラスを入力する TableAdapter の基底クラスを変更する<xref:System.ComponentModel.Component>で、**基底クラス**で TableAdapter のプロパティ、**データセット デザイナー**します。  
  
## <a name="tableadapter-methods-and-properties"></a>TableAdapter のメソッドとプロパティ  
 TableAdapter クラスはの一部、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]を探してようすることはできませんが、ドキュメント、または**オブジェクト ブラウザー**します。 このクラスは、デザイン時に、前述のいずれかのウィザードを使用することにより作成されます。 TableAdapter の作成時に TableAdapter に割り当てられる名前は、処理しているテーブルの名前に基づきます。 たとえば、`Orders` という名前のデータベース内にあるテーブルに基づいて TableAdapter を作成する場合、その TableAdapter の名前は、`OrdersTableAdapter` になります。 使用して、TableAdapter のクラス名を変更することができます、**名前**プロパティ、**データセット デザイナー**します。  
  
 TableAdapter で共通に使用されるメソッドとプロパティを次に示します。  
  
|メンバー|説明|  
|------------|-----------------|  
|`TableAdapter.Fill`|TableAdapter の関連付けられたデータ テーブルに、TableAdapter の SELECT コマンドの実行結果が格納されます。 詳細については、次を参照してください。[方法: データセットにデータ](../data-tools/how-to-fill-a-dataset-with-data.md)します。|  
|`TableAdapter.Update`|データベースに変更を送信し、更新の影響を受ける行の数を表す整数値を返します。 詳細については、次を参照してください。 [TableAdapter を使用してデータ更新](../data-tools/update-data-by-using-a-tableadapter.md)します。|  
|`TableAdapter.GetData`|データが格納された新しい <xref:System.Data.DataTable> を返します。|  
|`TableAdapter.Insert`|データ テーブル内に新しい行を作成します。 詳細については、次を参照してください。[方法: DataTable に行の追加](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf)します。|  
|`TableAdapter.ClearBeforeFill`|いずれかの `Fill` メソッドを呼び出す前に、データ テーブルが空になっているかどうかを確認します。|  
  
## <a name="tableadapter-update-method"></a>TableAdapter 更新メソッド  
 TableAdapter では、データ コマンドを使用して、データベースからの読み取りと書き込みを実行します。 TableAdapter の最初の `Fill` (メイン) クエリは、関連データ テーブルのスキーマや `InsertCommand` に関連付けられた `UpdateCommand`、`DeleteCommand`、および `TableAdapter.Update` の各コマンドを作成する基になります。 つまり、呼び出す TableAdapter の`Update`メソッド、TableAdapter が構成されているし、追加のクエリのない 1 つを追加するときに作成するステートメントの実行、 **TableAdapter クエリ構成ウィザード**.  
  
 TableAdapter を使用すると、通常実行するコマンド操作を効果的に実行できます。 たとえば、アダプターの `Fill` メソッドを呼び出すと、その `SelectCommand` プロパティに設定されているデータ コマンドがアダプターによって実行され、データ リーダー (<xref:System.Data.SqlClient.SqlDataReader> など) によって結果セットがデータ テーブルに読み込まれます。 同様に、アダプターの `Update` メソッドを呼び出すと、データ テーブル内で変更された各レコードに対して、`UpdateCommand`、`InsertCommand`、および `DeleteCommand` の各プロパティに設定されている適切なコマンドが実行されます。  
  
> [!NOTE]
>  メインのクエリに十分な情報がある場合、TableAdapter の生成時に既定で `InsertCommand`、`UpdateCommand`、および `DeleteCommand` の各コマンドが作成されます。 TableAdapter のメインのクエリが単一のテーブル SELECT ステートメントより複雑な場合、デザイナーで `InsertCommand`、`UpdateCommand`、および `DeleteCommand` を生成できないことがあります。 これらのコマンドが生成されていない場合、`TableAdapter.Update` メソッドの実行時にエラーが発生します。  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter の GenerateDbDirectMethods  
 `InsertCommand`、`UpdateCommand`、および `DeleteCommand` 以外に、データベースに対して直接実行できるメソッドも、TableAdapter に設定できます。 これらのメソッド (`TableAdapter.Insert`、`TableAdapter.Update`、および `TableAdapter.Delete`) は、データベース内でデータを直接操作するために呼び出すことができます。 つまり、TableAdapter.Update を呼び出して関連するデータ テーブルに対して保留になっている挿入、更新、および削除を処理するのではなく、これらの個別のメソッドをコードから呼び出すことができます。  
  
 これらのダイレクト メソッドを作成しない場合の設定、TableAdapter の**GenerateDbDirectMethods**プロパティを`false`(で、**プロパティ**ウィンドウ)。 TableAdapter に追加されるその他のクエリはスタンドアロン クエリであり、これらのメソッドを生成しません。  
  
## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter での Null 許容型のサポート  
 TableAdapter は、Null 許容型の `Nullable(Of T)` および `T?` をサポートしています。 Visual Basic での null 許容型の詳細については、次を参照してください。 [null 許容値型](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)します。 C# の null 許容型の詳細については、次を参照してください。 [null 許容型を使用して](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28)します。  
  
## <a name="see-also"></a>関連項目  
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [チュートリアル: データベース (Windows フォーム) 内のデータへの接続](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)