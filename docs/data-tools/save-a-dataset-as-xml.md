---
title: データセットを XML として保存 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b9d91e964ddade89c8bce8f0519517995b7d75a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="save-a-dataset-as-xml"></a>データセットを XML として保存します。
データセット内の XML データは、データセットで使用可能な XML メソッドを呼び出すことによりアクセスできます。 XML 形式で、データを保存する、いずれかを呼び出すことができます、<xref:System.Data.DataSet.GetXml%2A>メソッドまたは<xref:System.Data.DataSet.WriteXml%2A>のメソッド、<xref:System.Data.DataSet>です。  
  
 呼び出す、<xref:System.Data.DataSet.GetXml%2A>メソッドを XML としてフォーマットされているデータセット内のすべてのデータ テーブルからデータを含む文字列を返します。  
  
 呼び出す、<xref:System.Data.DataSet.WriteXml%2A>メソッドは、指定したファイルに XML 形式のデータを送信します。  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>変数にデータセットの XML 形式のデータを保存するには  
  
-   <xref:System.Data.DataSet.GetXml%2A>メソッドを返します、<xref:System.String>です。これは、型の変数を宣言することを意味<xref:System.String>の結果を割り当てると、<xref:System.Data.DataSet.GetXml%2A>メソッドです。  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>データセットのデータを XML 形式でファイルに保存するには  
  
-   <xref:System.Data.DataSet.WriteXml%2A>メソッドいくつかのオーバー ロードがあります。 次のコードでは、データをファイルに保存する方法を示します。変数を宣言し、ファイルを保存する有効なパスを割り当てます。  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## <a name="see-also"></a>関連項目  
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)