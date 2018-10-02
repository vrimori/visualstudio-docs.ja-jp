---
title: Tableadapter を使用してデータセットを入力 |Microsoft Docs
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
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c25bbba01d89935044e82a67b3ce40f99d1bf9a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548699"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Tableadapter を使用してデータセットを入力します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Tableadapter を使用してデータセットを入力](https://docs.microsoft.com/visualstudio/data-tools/fill-datasets-by-using-tableadapters)します。  
  
  
TableAdapter のコンポーネントでは、基に 1 つまたは複数のクエリまたは指定したストアド プロシージャ、データベースからデータを含むデータセットが表示されます。 Tableadapter を実行できますも追加、更新、およびデータセットに対して行った変更を保持するには、データベースを削除します。 特定のテーブルに関連のないグローバル コマンドを発行することもできます。  
  
> [!NOTE]
>  Tableadapter は、Visual Studio のデザイナーによって生成されます。 データセットをプログラムで作成する場合は、.NET Framework クラス、DataAdapter を使用します。  
  
 TableAdapter の操作の詳細については、次のトピックのいずれかに直接スキップできます。  
  
|トピック|説明|  
|-----------|-----------------|  
|[Tableadapter の作成および構成](../data-tools/create-and-configure-tableadapters.md)|デザイナーを使用して作成し、Tableadapter を構成する方法|  
|[パラメーター付きの TableAdapter クエリを作成する](../data-tools/create-parameterized-tableadapter-queries.md)|TableAdapter のプロシージャまたはクエリに引数を指定するユーザーを有効にする方法|  
|[TableAdapter で直接データベースにアクセスする](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Tableadapter の Dbdirect メソッドを使用する方法|  
|[データセットの読み込み中に制約をオフにする](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|データを更新するときに、foreign key 制約を使用する方法|  
|[TableAdapter の機能を拡張する方法](../data-tools/fill-datasets-by-using-tableadapters.md)|Tableadapter にカスタム コードを追加する方法|  
|[XML データのデータセットへの読み込み](../data-tools/read-xml-data-into-a-dataset.md)|XML を操作する方法|  
  
## <a name="tableadapters-overview"></a>TableAdapter の概要  
 Tableadapter は、データベース、クエリの実行またはストアド プロシージャに接続して、返されたデータをデータ テーブルを入力するデザイナーで生成されるコンポーネントです。 Tableadapter では、元のデータベースに、アプリケーションから更新されたデータを送信することもできます。 TableAdapter が関連付けられているテーブルのスキーマに準拠するデータを返す限り、TableAdapter に好きなだけ多くのクエリを実行することができます。 次の図は、Tableadapter がデータベースおよびメモリ内の他のオブジェクトとやり取りする方法を示しています。  
  
 ![クライアント アプリケーションでのデータ フロー](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Tableadapter は設計されています中に、**データセット デザイナー**、TableAdapter のクラスは、の入れ子になったクラスとしては生成されません<xref:System.Data.DataSet>します。 各データセットに固有の個別の名前空間内にあります。 たとえば、という名前のデータセットがある場合`NorthwindDataSet`、Tableadapter に関連付けられている<xref:System.Data.DataTable>内、`NorthwindDataSet`内であるか、`NorthwindDataSetTableAdapters`名前空間。 プログラムで特定の TableAdapter にアクセスするには、TableAdapter の新しいインスタンスを宣言する必要があります。 例えば:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>関連付けられた DataTable スキーマ  
 TableAdapter を作成するとき、最初のクエリを使用して、TableAdapter のスキーマを定義するストアド プロシージャに関連付けられた<xref:System.Data.DataTable>します。 この最初のクエリを実行するか、ストアド プロシージャを呼び出して、TableAdapter の`Fill`メソッド (TableAdapter の値を格納する機能に関連付けられた<xref:System.Data.DataTable>)。 TableAdapter のメイン クエリに加えられた変更は、関連付けられたデータ テーブルのスキーマに反映されます。 たとえば、メイン クエリから列を削除しても列から削除関連付けられたデータ テーブル。 TableAdapter に関する他のクエリは、メインのクエリにない列を返す SQL ステートメントを使用して、デザイナーは、メインのクエリとその他のクエリの列の変更を同期しようとします。 詳細については、次を参照してください。[方法: Tableadapter の編集](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)します。  
  
## <a name="tableadapter-update-commands"></a>TableAdapter 更新コマンド  
 TableAdapter の更新機能では、情報の量は、TableAdapter ウィザードで、メイン クエリで使用できるに依存します。 たとえば、複数のテーブル (JOIN)、スカラー値、ビュー、または集約関数の結果から値をフェッチするように設定された TableAdapter の場合、最初の作成時には、基になるデータベースに更新を戻す機能がありません。 ただし、手動で INSERT、UPDATE、および DELETE コマンドを構成することができます、**プロパティ**ウィンドウ。  
  
## <a name="tableadapter-queries"></a>TableAdapter クエリ  
 ![複数のクエリによる TableAdapter](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Tableadapter には、複数のクエリ、関連するデータ テーブルの入力を含めることができます。 それぞれのクエリが、関連するデータ テーブルと同じスキーマに従ったデータを返す限り、アプリケーションに必要なクエリをいくつでも TableAdapter に定義できます。 この機能には、異なる条件に基づいて異なる結果を読み込む TableAdapter が有効にします。  
  
 たとえば、アプリケーションに顧客名を持つテーブルが含まれている場合と同じ状態にあるすべての顧客テーブルに格納する別の特定の文字で始まるすべての顧客名とテーブルに格納するクエリを作成できます。 入力する、`Customers`テーブルを特定の状態でお客様と作成することができます、`FillByState`を次のように、状態の値のパラメーターを受け取るクエリ:`SELECT * FROM Customers WHERE State = @State`します。 呼び出すことによって、クエリを実行する、`FillByState`メソッドとパラメーターの値に渡す次のような:`CustomerTableAdapter.FillByState("WA")`します。  
  
 TableAdapter のデータ テーブルと同じスキーマのデータを返すクエリを追加するだけでは、スカラー (単一) 値を返すクエリを追加できます。 たとえば、顧客の数を返すクエリ (`SELECT Count(*) From Customers`) は有効です、`CustomersTableAdapter,`場合でも、返されるデータは、テーブルのスキーマに適合していません。  
  
## <a name="clearbeforefill-property"></a>ClearBeforeFill プロパティ  
 既定では、既存のデータを消去すると、TableAdapter のデータ テーブルを格納するクエリを実行するたびに、クエリの結果のみがテーブルに読み込まれます。 TableAdapter の設定`ClearBeforeFill`プロパティを`false`を追加または既存のデータをデータ テーブルにクエリから返されるデータをマージするかどうか。 データを消去するかどうかに関係なく必要があります、データベースに更新プログラムを明示的に送信する場合は、それらを保存します。 テーブルに格納する別のクエリを実行する前に、テーブル内のデータに変更を保存してください。 詳細については、次を参照してください。 [TableAdapter を使用してデータ更新](../data-tools/update-data-by-using-a-tableadapter.md)します。  
  
## <a name="tableadapter-inheritance"></a>TableAdapter の継承  
 Tableadapter では、標準のデータ アダプターの機能を拡張、構成をカプセル化して<xref:System.Data.Common.DataAdapter>クラスか? qualifyHint = False & autoUpgrade = True。 TableAdapter が継承、既定で、<xref:System.ComponentModel.Component>クラスおよびにキャストすることはできません、<xref:System.Data.Common.DataAdapter>クラス。 TableAdapter をキャスト、<xref:System.Data.Common.DataAdapter>で結果のクラス、<xref:System.InvalidCastException>エラー? qualifyHint = False & autoUpgrade = True。 派生したクラスを入力する TableAdapter の基底クラスを変更する<xref:System.ComponentModel.Component>で、**基底クラス**で TableAdapter のプロパティ、**データセット デザイナー**します。  
  
## <a name="tableadapter-methods-and-properties"></a>TableAdapter のメソッドとプロパティ  
 TableAdapter クラスはの一部、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]します。 つまり、ドキュメントを検索できない、または**オブジェクト ブラウザー**します。 前に説明したウィザードの 1 つを使用すると、デザイン時に作成されます。 作成するときに、TableAdapter に割り当てられている名前は、使用しているテーブルの名前に基づきます。 たとえば、という名前のデータベース内のテーブルに基づいて TableAdapter を作成する`Orders`、TableAdapter の名前は`OrdersTableAdapter`します。 使用して、TableAdapter のクラス名を変更することができます、**名前**プロパティ、**データセット デザイナー**します。  
  
 一般的に使用されるメソッドと Tableadapter のプロパティを次に示します。  
  
|メンバー|説明|  
|------------|-----------------|  
|`TableAdapter.Fill`|TableAdapter の関連付けられたデータ テーブルに、TableAdapter の SELECT コマンドの実行結果が格納されます。|  
|`TableAdapter.Update`|データベースに変更を送信し、更新によって影響を受ける行の数を表す整数を返します。 詳細については、次を参照してください。 [TableAdapter を使用してデータ更新](../data-tools/update-data-by-using-a-tableadapter.md)します。|  
|`TableAdapter.GetData`|新しいを返します<xref:System.Data.DataTable>データが格納されます。|  
|`TableAdapter.Insert`|データ テーブル内に新しい行を作成します。 詳細については、次を参照してください。[データベースに新しいレコードを挿入](../data-tools/insert-new-records-into-a-database.md)します。|  
|`TableAdapter.ClearBeforeFill`|いずれかの `Fill` メソッドを呼び出す前に、データ テーブルが空になっているかどうかを確認します。|  
  
## <a name="tableadapter-update-method"></a>TableAdapter 更新メソッド  
 TableAdapter では、データ コマンドを使用して、データベースからの読み取りと書き込みを実行します。 TableAdapter の最初`Fill`(メイン) クエリが、関連付けられているデータ テーブルのスキーマの作成の基礎として使用だけでなく`InsertCommand`、 `UpdateCommand`、および`DeleteCommand`コマンドに関連付けられている、`TableAdapter.Update`メソッド。 呼び出す TableAdapter の`Update`メソッド、TableAdapter があったときに作成されたステートメントを実行する構成、追加のクエリに追加されたいずれ、 **TableAdapter クエリ構成ウィザード**.  
  
 TableAdapter を使用すると、通常実行するコマンド操作を効果的に実行できます。 たとえば、アダプターを呼び出すと`Fill`メソッドでは、アダプターのデータでコマンドを実行その`SelectCommand`プロパティ データ リーダーを使用して (たとえば、 <xref:System.Data.SqlClient.SqlDataReader>) データ テーブルに結果セットを読み込めません。 同様に、アダプターを呼び出すと`Update`メソッドでは、適切なコマンド実行 (で、 `UpdateCommand`、 `InsertCommand`、および`DeleteCommand`プロパティ) の各データ テーブル内のレコードを変更します。  
  
> [!NOTE]
>  メインのクエリに十分な情報がある場合、TableAdapter の生成時に既定で `InsertCommand`、`UpdateCommand`、および `DeleteCommand` の各コマンドが作成されます。 TableAdapter のメインのクエリが 1 つのテーブルの SELECT ステートメントを超える場合は、デザイナーは生成できませんは`InsertCommand`、 `UpdateCommand`、および`DeleteCommand`します。 実行するときにエラーが発生する場合、これらのコマンドは生成されません、`TableAdapter.Update`メソッド。  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter の GenerateDbDirectMethods  
 ほかに`InsertCommand`、 `UpdateCommand`、および`DeleteCommand`Tableadapter は、データベースに対して直接実行できるメソッドで作成されます。 これらのメソッド (`TableAdapter.Insert`、`TableAdapter.Update`、および `TableAdapter.Delete`) は、データベース内でデータを直接操作するために呼び出すことができます。 つまり、これらの各メソッドを呼び出す代わりにコードから呼び出すことができます`TableAdapter.Update`挿入、更新、および保留になっている削除を処理するために関連付けられたデータ テーブルにします。  
  
 これらのダイレクト メソッドを作成しない場合は、設定、TableAdapter の**GenerateDbDirectMethods**プロパティを`false`(で、**プロパティ**ウィンドウ)。 TableAdapter に追加される追加のクエリはスタンドアロン クエリなど、これらのメソッドを生成しません。  
  
## <a name="tableadapter-support-for-nullable-types"></a>Null 許容型の TableAdapter のサポート  
 Null 許容型をサポートする Tableadapter`Nullable(Of T)`と`T?`します。 Visual Basic での null 許容型について詳しくは、「[null 許容値型](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)」をご覧ください。 C# の null 許容型の詳細については、次を参照してください。 [null 許容型を使用して](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28)します。  
  
## <a name="security"></a>セキュリティ  
 データ コマンドを使用すると、`CommandType`プロパティに設定<xref:System.Data.CommandType>、慎重に、データベースに渡す前に、クライアントから送信される情報を確認します。 悪意のあるユーザーが、承認なしでデータベースにアクセスしたり、データベースを破壊したりする目的で、変更した SQL ステートメントや追加の SQL ステートメントの送信 (挿入) を試みる場合があります。 ユーザーの入力をデータベースを転送する前に常に情報が有効なことを確認します。 常にパラメーター化クエリまたは可能であればストアド プロシージャを使用することをお勧めします。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)

