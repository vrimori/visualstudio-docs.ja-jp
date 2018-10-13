---
title: '方法: 特定のバージョンの DataRow を取得 |Microsoft Docs'
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
- row states
- updating datasets, row states
- DataRow object
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 5bd8ae12c77c671e375043a0381a4b580d1a03d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255490"
---
# <a name="how-to-get-specific-versions-of-a-datarow"></a>方法 : 特定のバージョンの DataRow を取得する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

データ行を変更すると、データセットにその行の元のバージョン (<xref:System.Data.DataRowVersion>) と新しいバージョン (<xref:System.Data.DataRowVersion>) が保存されます。 たとえば、`AcceptChanges` メソッドを呼び出す前にレコードの別のバージョン (<xref:System.Data.DataRowVersion> 列挙定数で定義) にアクセスし、そのバージョンに応じて変更を処理できます。  
  
> [!NOTE]
>  別のバージョンの行が存在するのは、その行を編集してから `AcceptChanges` メソッドを呼び出すまでの間です。 `AcceptChanges` メソッドの呼び出し後は、現在のバージョンと元のバージョンが同じになります。  
  
 <xref:System.Data.DataRowVersion> 値を列インデックス (文字列である列名) と共に渡すと、その列の特定の行バージョンから値が返されます。 変更された列は <xref:System.Data.DataTable.ColumnChanging> イベントおよび <xref:System.Data.DataTable.ColumnChanged> イベント中に識別されるため、検証の目的で行バージョンの違いを簡単に調べることができます。 ただし、一時的に制約を中断しているときはこれらのイベントは発生しないため、変更された列をプログラムで識別する必要があります。 <xref:System.Data.DataTable.Columns%2A> コレクションを反復処理し、異なる <xref:System.Data.DataRowVersion> 値を比較することにより変更された列を識別できます。  
  
## <a name="accessing-the-original-version-of-a-datarow"></a>DataRow の元のバージョンへのアクセス  
  
#### <a name="to-get-the-original-version-of-a-record"></a>レコードの元のバージョンを取得するには  
  
-   取得する行の <xref:System.Data.DataRowVersion> を渡して列の値にアクセスします。  
  
     <xref:System.Data.DataRowVersion> 値を使って、`CompanyName` の <xref:System.Data.DataRow> フィールドの元の値を取得する例を次に示します。  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="accessing-the-current-version-of-a-datarow"></a>DataRow の現在のバージョンへのアクセス  
  
#### <a name="to-get-the-current-version-of-a-record"></a>レコードの現在のバージョンを取得するには  
  
-   列の値にアクセスし、取得する行のバージョンを示すインデックスに対するパラメーターを追加します。  
  
     <xref:System.Data.DataRowVersion> 値を使って、`CompanyName` の <xref:System.Data.DataRow> フィールドの現在の値を取得する例を次に示します。  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>関連項目  
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)   
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)