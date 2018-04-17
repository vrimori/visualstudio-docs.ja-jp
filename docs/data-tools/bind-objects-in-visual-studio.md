---
title: Visual Studio でのオブジェクトのバインド |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 71922f3fb6dffb63c1a6c5ed1b12e5cbce402323
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="bind-objects-in-visual-studio"></a>Visual Studio でのオブジェクトのバインド
Visual Studio は、アプリケーションでデータ ソースとして、カスタム オブジェクトを使用するためのデザイン時ツールを提供します。 UI コントロールにバインドされているオブジェクトに、データベースからデータを格納する場合は、Entity Framework を使用して、または複数のクラスを生成することをお勧めします。 Entity Framework は、すべて、定型的な変更の追跡は、コード、DbSet オブジェクトで AcceptChanges を呼び出すときにローカルのオブジェクトへの変更が、データベースに保持自動的を自動で生成します。 詳細については、次を参照してください。 [Entity Framework ドキュメント](https://ef.readthedocs.org/en/latest/)です。  
  
> [!TIP]
>  アプリケーションが既にデータセットに基づいている場合にのみ、この記事でオブジェクトのバインドする方法を検討してください。これらの方法は、慣れて既にデータセット、および処理するデータが表形式および複雑すぎるか大きすぎる場合にも使用できます。 オブジェクトに直接 DataReader を使用して、手動でデータ バインド、せず、UI を更新してデータの読み込みに関連する、さらに簡単な例については、次を参照してください。 [ADO.NET を使用して単純なデータ アプリケーションを作成する](../data-tools/create-a-simple-data-application-by-using-adonet.md)です。  
  
## <a name="object-requirements"></a>オブジェクトの要件  
 Visual Studio でのデザイン ツールにこのデータを使用するカスタム オブジェクトの唯一の要件は、オブジェクトに少なくとも 1 つのパブリック プロパティが必要があることです。  
  
 一般に、カスタム オブジェクトでは、任意の特定のインターフェイス、コンス トラクター、またはアプリケーションのデータ ソースとして機能する属性は必要ありません。 ただしからオブジェクトをドラッグする場合、**データソース**データ バインド コントロールを作成するデザイン サーフェイスにウィンドウ オブジェクトを実装する場合と、<xref:System.ComponentModel.ITypedList>または<xref:System.ComponentModel.IListSource>インターフェイス、オブジェクトは、既定値を持つ必要がありますコンス トラクターです。 それ以外の場合、Visual Studio は、データ ソース オブジェクトをインスタンス化できませんし、デザイン サーフェイスに項目をドラッグするときにエラーが表示されます。  
  
## <a name="examples-of-using-custom-objects-as-data-sources"></a>データ ソースとしてカスタム オブジェクトを使用する例  
 データ ソースとして、オブジェクトを使用する際に、アプリケーション ロジックを実装する方法は数多くはありますが、SQL データベースがありますは簡略化すれば、Visual Studio によって生成された TableAdapter オブジェクトを使用して、いくつかの標準的な操作です。 このページは、これらの標準的なプロセスを実装する方法を説明します。 TableAdapters.It を使用するものではありませんガイドとして、カスタム オブジェクトを作成するためです。 たとえば、通常行うには、オブジェクト、またはアプリケーションのロジックの特定の実装に関係なく次の標準的な操作。  
  
-   (通常はデータベース) からオブジェクトにデータを読み込んでいます。  
  
-   オブジェクトの型指定されたコレクションを作成します。  
  
-   オブジェクトを追加し、オブジェクトのコレクションから削除します。  
  
-   フォーム上のユーザーに、オブジェクトのデータを表示しています。  
  
-   オブジェクト内のデータを変更または編集します。  
  
-   オブジェクトからデータベースにデータを保存します。   
  
### <a name="load-data-into-objects"></a>オブジェクトにデータを読み込む  
 この例では、Tableadapter を使用して、オブジェクトにデータを読み込みます。 既定では、Tableadapter は、次の 2 つの種類のデータベースからデータをフェッチし、データ テーブルを設定するメソッドで作成されます。  
  
-   `TableAdapter.Fill`メソッドが返されるデータで既存のデータ テーブルを塗りつぶします。  
  
-   `TableAdapter.GetData`メソッドは、データが設定される新しいデータ テーブルを返します。  
  
 最も簡単な方法、カスタム オブジェクトにデータを読み込むを呼び出す、`TableAdapter.GetData`メソッドが返されたデータ テーブル内の行のコレクションをループし、各行の値の各オブジェクトを設定します。 作成することができます、 `GetData` TableAdapter に追加された任意のクエリのデータが設定されたテーブルを返すメソッド。  
  
> [!NOTE]
>  Visual Studio は、TableAdapter クエリを名前`Fill`と`GetData`既定では、それらの名前は任意の有効なメソッド名を変更することができます。  
  
 次の例では、データ テーブルの行をループし、データを持つオブジェクトを設定する方法を示します。  
  
 [!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### <a name="create-a-typed-collection-of-objects"></a>オブジェクトの型指定されたコレクションを作成します。  
 オブジェクトのコレクション クラスを作成するかによって自動的に提供される型指定されたコレクションを使用して、 [BindingSource コンポーネント](/dotnet/framework/winforms/controls/bindingsource-component)です。  
  
 継承することをお勧めのオブジェクトのカスタム コレクション クラスを作成する場合は、<xref:System.ComponentModel.BindingList%601>です。 このジェネリック クラスは、Windows フォームでデータ バインド インフラストラクチャに通知を送信するイベントを発生させる機能と同様に、コレクションを管理する機能を提供します。  
  
 自動的に生成されたコレクション、<xref:System.Windows.Forms.BindingSource>を使用して、<xref:System.ComponentModel.BindingList%601>の型指定されたコレクション。 アプリケーションに、追加の機能は必要ないかどうかは、内に、コレクションを管理することができます、<xref:System.Windows.Forms.BindingSource>です。 詳細については、次を参照してください。、<xref:System.Windows.Forms.BindingSource.List%2A>のプロパティ、<xref:System.Windows.Forms.BindingSource>クラスです。  
  
> [!NOTE]
>  かどうか、コレクションの基本実装では提供されない機能が必要です、 <xref:System.ComponentModel.BindingList%601>、必要に応じて、クラスに追加できるように、カスタム コレクションを作成する必要があります。  
  
 次のコードは、厳密に型指定されたコレクションのためのクラスを作成する方法を示します`Order`オブジェクト。  
  
 [!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### <a name="add-objects-to-a-collection"></a>オブジェクトをコレクションに追加します。  
 呼び出して、オブジェクトをコレクションに追加する、`Add`またはのカスタム コレクション クラスのメソッド、<xref:System.Windows.Forms.BindingSource>です。  
  
 
> [!NOTE]
>  `Add`メソッドはから継承する場合、自動的にカスタム コレクションの提供<xref:System.ComponentModel.BindingList%601>です。  
  
 次のコードで型指定されたコレクションにオブジェクトを追加する方法を示しています、 <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 次のコードから継承する型指定されたコレクションにオブジェクトを追加する方法を示しています<xref:System.ComponentModel.BindingList%601>:。  
  
> [!NOTE]
>  この例では、`Orders`コレクションのプロパティは、`Customer`オブジェクト。  
  
 [!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### <a name="remove-objects-from-a-collection"></a>オブジェクトをコレクションから削除します。  
 呼び出すことによってコレクションからオブジェクトを削除する、`Remove`または`RemoveAt`メソッドか、カスタム コレクション クラスの<xref:System.Windows.Forms.BindingSource>します。  
  
> [!NOTE]
>  `Remove`と`RemoveAt`から継承する場合は、カスタム コレクション用のメソッドが自動的に提供<xref:System.ComponentModel.BindingList%601>です。  
  
 次のコードの検索し、に型指定されたコレクションからオブジェクトを削除する方法を示しています、<xref:System.Windows.Forms.BindingSource>で、<xref:System.Windows.Forms.BindingSource.RemoveAt%2A>メソッド。  
  
 [!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### <a name="display-object-data-to-users"></a>ユーザーにオブジェクト データを表示します。  
 データをユーザーにオブジェクトを表示する、データ ソースを使用してオブジェクトを作成、**データ ソースの構成**ウィザードで、オブジェクト全体または個々 のプロパティからフォームにドラッグし、**データソース**ウィンドウです。  
  
### <a name="modify-the-data-in-objects"></a>オブジェクト内のデータを変更します。  
 Windows フォーム コントロールにデータ バインドされたカスタム オブジェクトのデータを編集するには、(または、オブジェクトのプロパティに直接)、バインドされたコントロールでのデータを単に編集します。 データ バインディング アーキテクチャでは、オブジェクト内のデータを更新します。  
  
 アプリケーションには、変更の追跡と元の値に提案された変更のロールバックが必要とする場合は、オブジェクト モデルで、この機能を実装する必要があります。 どのデータ テーブルの提案された変更を追跡の例については、次を参照してください。 <xref:System.Data.DataRowState>、 <xref:System.Data.DataSet.HasChanges%2A>、および<xref:System.Data.DataTable.GetChanges%2A>です。  
  
### <a name="save-data-in-objects-back-to-the-database"></a>データベースにオブジェクト内のデータを保存します。  
 TableAdapter の DBDirect メソッドに、オブジェクトから値を渡すことによって、データベースにデータを保存します。  
  
 Visual Studio では、データベースに対して直接実行できる DBDirect メソッドを作成します。 これらのメソッドには、DataSet および DataTable オブジェクトは不要です。  
  
|TableAdapter DBDirect メソッド|説明|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|個々 の列の値をメソッド パラメーターとして渡すことを許可する、データベースに新しいレコードを追加します。|  
|`TableAdapter.Update`|既存のデータベース内のレコードを更新します。 元と新しい列の値は、Update メソッドは、メソッドのパラメーターとして受け取ります。 元の値は、元のレコードを検索するために使用され、そのレコードを更新する、新しい値が使用されます。<br /><br /> `TableAdapter.Update`実行することで、データベースにデータセットの変更を調整するためにメソッドを使用しても、 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、 <xref:System.Data.DataRow>、または配列の<xref:System.Data.DataRow>メソッド パラメーターとして。|  
|`TableAdapter.Delete`|メソッドのパラメーターとして渡された元の列値に基づいて、データベースから既存のレコードを削除します。|  
  
 オブジェクトのコレクションからデータを保存するには、(たとえば、次のループを使用して) オブジェクトのコレクションをループします。TableAdapter の DBDirect メソッドを使用して、データベースに各オブジェクトの値を送信します。  
  
 次の例を使用する方法を示しています、 `TableAdapter.Insert` DBDirect メソッドを直接データベースに新しい顧客を追加します。  
  
 [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)