---
title: Visual Studio でのオブジェクトのバインド |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c832686cbe56bb9d2a3b9f31206dada8043e7b44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918637"
---
# <a name="bind-objects-in-visual-studio"></a>Visual Studio でのオブジェクトのバインド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio には、アプリケーションでデータ ソースとしてカスタム オブジェクトを操作するためのデザイン時ツールが用意されています。 UI コントロールにバインドするオブジェクトに、データベースからデータを格納する場合は、Entity Framework を使用して、クラスまたはクラスを生成することをお勧めします。 エンティティ Frameworkautogenerates すべて、定型コード変更の追跡は、コード、ローカルのオブジェクトに変更されるいずれかは、DbSet オブジェクトで AcceptChanges を呼び出すときに自動的にデータベースに保存されます。    詳細については、次を参照してください。 [Entity Framework ドキュメント](https://ef.readthedocs.org/en/latest/)します。  
  
> [!TIP]
>  アプリケーションは既にデータセットに基づいている場合にのみ、この記事では、オブジェクトのバインドするためのアプローチを検討してください。これらの方法は、データセット、理解しているし、処理するデータが表形式と複雑すぎるか大きすぎる場合にも使用できます。 DataReader によるデータ バインド、なし、UI を手動で更新してオブジェクトに直接データの読み込みに関連する、さらに簡単な例については、次を参照してください。 [ADO.NET を使用して単純なデータ アプリケーションを作成する](../data-tools/create-a-simple-data-application-by-using-adonet.md)します。  
  
## <a name="object-requirements"></a>オブジェクトの要件  
 Visual Studio でデザイン ツールをデータを処理するカスタム オブジェクトの唯一の要件は、オブジェクトが少なくとも 1 つのパブリック プロパティを必要があることです。  
  
 一般に、カスタム オブジェクトでは、任意の特定のインターフェイス、コンス トラクター、またはアプリケーションのデータ ソースとして機能する属性は必要ありません。 ただしからオブジェクトをドラッグする場合、**データソース**ウィンドウは、データ バインド コントロールを作成するデザイン サーフェイスにオブジェクトを実装する場合と、<xref:System.ComponentModel.ITypedList>または<xref:System.ComponentModel.IListSource>インターフェイス、オブジェクトには、既定値が必要コンス トラクターです。 それ以外の場合、Visual Studio は、データ ソース オブジェクトをインスタンス化できないし、デザイン サーフェイスに項目をドラッグすると、エラーが表示されます。  
  
## <a name="examples-of-using-custom-objects-as-data-sources"></a>カスタム オブジェクトを使用して、データ ソースとして例を示します  
 データ ソースとしてオブジェクトを使用する場合、アプリケーション ロジックを実装する方法を使用して、SQL のデータベースがありますが Visual Studio が生成する TableAdapter のオブジェクトを使用して簡略化できますが、いくつかの標準的な操作です。 このページは、これらの標準的なプロセスを実装する方法を説明します。 TableAdapters.It を使用するものではありませんをガイドとして、カスタム オブジェクトを作成するためです。 たとえば、オブジェクト、またはアプリケーションのロジックの特定の実装に関係なく次の標準的な操作を通常実行は。  
  
-   (通常はデータベース) からオブジェクトにデータを読み込んでいます。  
  
-   オブジェクトの型指定されたコレクションを作成します。  
  
-   オブジェクトを追加し、オブジェクトのコレクションから削除します。  
  
-   フォーム上のユーザーにオブジェクト データを表示しています。  
  
-   オブジェクトのデータを変更または編集します。  
  
-   オブジェクトからデータベースにデータを保存しています。  
  
> [!NOTE]
>  次の手順をお勧めをより理解、および、このページの例については、コンテキストを提供する、するには:[チュートリアル: データ オブジェクト (Windows フォーム) に接続する](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)します。 このチュートリアルでは、ここで説明したオブジェクトを作成します。  
  
### <a name="loaddata-into-objects"></a>オブジェクトに Loaddata  
 この例では、Tableadapter を使用して、オブジェクトにデータを読み込みます。 既定では、Tableadapter は、2 つの種類のデータベースからデータをフェッチし、データ テーブルを設定するメソッドで作成されます。  
  
- `TableAdapter.Fill`メソッドが返されるデータで既存のデータ テーブルを塗りつぶします。  
  
- `TableAdapter.GetData`メソッドは、データが格納されて、新しいデータ テーブルを返します。  
  
  呼び出すことをカスタム オブジェクトにデータを読み込む最も簡単な方法です、`TableAdapter.GetData`メソッド、返されたデータ テーブル内の行のコレクションをループ処理し、各行の値では、各オブジェクトに設定します。 作成することができます、 `GetData` TableAdapter に追加された任意のクエリのデータが設定されたデータ テーブルを返すメソッド。  
  
> [!NOTE]
>  Visual Studio は、TableAdapter クエリを名前`Fill`と`GetData`既定では、これらの名前は任意の有効なメソッド名を変更することができます。  
  
 次の例では、データ テーブルの行をループして、データを持つオブジェクトを設定する方法を示します。  
  
 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]  
  
### <a name="create-a-typed-collection-of-objects"></a>オブジェクトの型指定されたコレクションを作成します。  
 オブジェクトのコレクション クラスを作成するか、によって自動的に提供される型指定されたコレクションを使用することができます、 [BindingSource コンポーネント](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)します。  
  
 継承することをお勧めのオブジェクトのカスタム コレクション クラスを作成する場合は、<xref:System.ComponentModel.BindingList%601>します。 このジェネリック クラスは、Windows フォームでデータ バインド インフラストラクチャに通知を送信するイベントを発生させる機能と同様に、コレクションを管理する機能を提供します。  
  
 自動的に生成されたコレクション、<xref:System.Windows.Forms.BindingSource>を使用して、<xref:System.ComponentModel.BindingList%601>の型指定されたコレクション。 アプリケーションには、追加の機能が必要としないかどうかは、内のコレクションを維持することができます、<xref:System.Windows.Forms.BindingSource>します。 詳細については、次を参照してください。、<xref:System.Windows.Forms.BindingSource.List%2A>のプロパティ、<xref:System.Windows.Forms.BindingSource>クラス。  
  
> [!NOTE]
>  コレクションの基本実装によって提供されない機能が必要とかどうか、 <xref:System.ComponentModel.BindingList%601>、必要に応じて、クラスに追加できるように、カスタム コレクションを作成する必要があります。  
  
 次のコードは、クラスの厳密に型指定されたコレクションを作成する方法を示しています。`Order`オブジェクト。  
  
 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]  
  
### <a name="addobjects-to-a-collection"></a>コレクションに Addobjects  
 呼び出すことによって、オブジェクトをコレクションに追加する、`Add`またはのカスタム コレクション クラスのメソッド、<xref:System.Windows.Forms.BindingSource>します。  
  
 使用してコレクションに追加する例については、<xref:System.Windows.Forms.BindingSource>を参照してください、`LoadCustomers`メソッド[チュートリアル: データ オブジェクト (Windows フォーム) に接続する](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)します。  
  
 オブジェクトのカスタム コレクションに追加の例は、次を参照してください。、`LoadOrders`メソッド[チュートリアル: データ オブジェクト (Windows フォーム) に接続する](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)します。  
  
> [!NOTE]
>  `Add`メソッドはから継承する場合、自動的にカスタム コレクションの提供<xref:System.ComponentModel.BindingList%601>します。  
  
 次のコードでは、型指定されたコレクションにオブジェクトを追加する方法を示しています、 <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]  
  
 次のコードは、オブジェクトから継承する型指定されたコレクションを追加する方法を示しています<xref:System.ComponentModel.BindingList%601>:。  
  
> [!NOTE]
>  この例では、`Orders`コレクションのプロパティである、`Customer`オブジェクト。  
  
 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]  
  
### <a name="removeobjects-from-a-collection"></a>コレクションからの後  
 コレクションから呼び出すことによってオブジェクトを削除する、`Remove`または`RemoveAt`メソッドや、カスタム コレクション クラスの<xref:System.Windows.Forms.BindingSource>します。  
  
> [!NOTE]
>  `Remove`と`RemoveAt`から継承する場合、カスタム コレクション用のメソッドが自動的に提供<xref:System.ComponentModel.BindingList%601>します。  
  
 次のコードは、検索およびでは、型指定されたコレクションからオブジェクトを削除する方法を示しています、<xref:System.Windows.Forms.BindingSource>で、<xref:System.Windows.Forms.BindingSource.RemoveAt%2A>メソッド。  
  
 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]  
  
### <a name="displayobject-data-to-users"></a>ユーザーに Displayobject データ  
 データ ソースを使用してオブジェクトを作成、データをユーザーにオブジェクトを表示する、**データ ソースの構成**ウィザードからフォームに、オブジェクト全体または個々 のプロパティをドラッグし、**データソース**ウィンドウ。  
  
### <a name="modify-the-data-in-objects"></a>オブジェクト内のデータを変更します。  
 Windows フォーム コントロールにデータ バインドされたカスタム オブジェクトのデータを編集するには、単に、バインドされたコントロール (または、オブジェクトのプロパティで直接) データを編集します。 データ バインディング アーキテクチャでは、オブジェクト内のデータを更新します。  
  
 アプリケーションには、変更の追跡と元の値に提案された変更のロールバックが必要とする場合は、オブジェクト モデルで、この機能を実装する必要があります。 どのデータ テーブルの提案された変更を追跡の例については、次を参照してください。 <xref:System.Data.DataRowState>、 <xref:System.Data.DataSet.HasChanges%2A>、および<xref:System.Data.DataTable.GetChanges%2A>します。  
  
### <a name="savedata-in-objects-back-to-the-database"></a>元のデータベースにオブジェクトで Savedata  
 TableAdapter の DBDirect メソッドをオブジェクトから値を渡すことで、元のデータベースにデータを保存します。  
  
 Visual Studio では、データベースに対して直接実行できる DBDirect メソッドを作成します。 これらのメソッドは、DataSet または DataTable オブジェクトには必要ありません。  
  
|TableAdapter DBDirect メソッド|説明|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|個々 の列の値をメソッド パラメーターとして渡すことができるように、データベースに新しいレコードを追加します。|  
|`TableAdapter.Update`|既存のデータベース内のレコードを更新します。 元と新しい列の値は、Update メソッドは、メソッドのパラメーターとして受け取ります。 元のレコードを検索するため、元の値と新しい値は、そのレコードの更新に使用されます。<br /><br /> `TableAdapter.Update`ことで、データベースにデータセットの変更を調整するメソッドを使用しても、 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、 <xref:System.Data.DataRow>、または配列の<xref:System.Data.DataRow>メソッドのパラメーターとして。|  
|`TableAdapter.Delete`|メソッドのパラメーターとして渡された元の列の値に基づいて、データベースから既存のレコードを削除します。|  
  
 オブジェクトのコレクションからデータを保存するには、(たとえば、次のループを使用して) オブジェクトのコレクションをループします。TableAdapter の DBDirect メソッドを使用して、各オブジェクトの値をデータベースに送信します。  
  
 次の例は、使用する方法を示します、 `TableAdapter.Insert` DBDirect メソッドを直接データベースに新しい顧客を追加します。  
  
 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)

