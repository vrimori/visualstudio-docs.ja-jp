---
title: '方法: データセットの変更をコミット |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataSet.AcceptChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], committing changes
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 40acd2a706ef7bc00ea1f90e51e90705be5658c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540111"
---
# <a name="how-to-commit-changes-in-a-dataset"></a>方法 : データセットの変更をコミットする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

データセット内のレコードを更新、挿入、レコードを削除して変更を行い、データセットは、レコードの元と現在のバージョンを保持します。 さらに、各行の<xref:System.Data.DataRow.RowState%2A>レコードは、元の状態でまたはが更新、挿入、または削除されたかどうかの追跡プロパティ。 この情報は、特定のバージョンの行を検索する必要がある場合に便利です。 通常、別のプロセスに送信するすべての変更されたレコードのサブセットを取得します。 詳細については、次を参照してください。[方法: 変更された行の取得](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)します。 呼び出すことによって、変更をコミットするには、すべての変更された行を処理した後、`AcceptChanges`のメソッド、 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、または<xref:System.Data.DataRow>します。 `AcceptChanges`の update メソッドを呼び出すときに自動的に呼び出されるメソッドを[TableAdapter](../data-tools/tableadapter-overview.md)またはデータ アダプター。 呼び出す`AcceptChanges`データベースへの変更を送信した後にします。  
  
 呼び出すと<xref:System.Data.DataSet.AcceptChanges%2A>上、 <xref:System.Data.DataSet>、any<xref:System.Data.DataRow>まだ編集モードでのオブジェクトが正常にそれらの編集を終了します。 <xref:System.Data.DataRow.RowState%2A>の各プロパティ<xref:System.Data.DataRow>も変更します。<xref:System.Data.DataRowState>と<xref:System.Data.DataRowState>になる行<xref:System.Data.DataRowState>、および<xref:System.Data.DataRowState>行が削除されます。  
  
 場合、<xref:System.Data.DataSet>が含まれています<xref:System.Data.ForeignKeyConstraint>オブジェクトを呼び出し、<xref:System.Data.DataSet.AcceptChanges%2A>メソッドとも、<xref:System.Data.AcceptRejectRule>を適用します。  
  
### <a name="to-commit-changes-in-a-dataset"></a>データセットの変更をコミットするには  
  
-   呼び出す、`AcceptChanges`いずれかのメソッド、 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、または<xref:System.Data.DataRow>それらのオブジェクトの変更をコミットします。  
  
     次の例を呼び出す方法を示しています、`AcceptChanges`の変更をコミットする方法、`Customers`データ ソースの更新後のテーブル。  
  
     [!code-csharp[VbRaddataEditing#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#11)]
     [!code-vb[VbRaddataEditing#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#11)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [データの保存](../data-tools/saving-data.md)   
 [方法: 変更された行の取得](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)