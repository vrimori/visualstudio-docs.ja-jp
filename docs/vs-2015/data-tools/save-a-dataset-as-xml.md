---
title: データセットを XML として保存 |Microsoft Docs
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
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bfea6a97dd5126216d5163dee1dc17e5f6364b46
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533668"
---
# <a name="save-a-dataset-as-xml"></a>データセットを XML として保存する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[データセットを XML として保存](https://docs.microsoft.com/visualstudio/data-tools/save-a-dataset-as-xml)します。  
  
  
データセット内の XML データは、データセットで使用可能な XML メソッドを呼び出すことによってアクセスできます。 XML 形式でデータを保存する、いずれかを呼び出すことができます、<xref:System.Data.DataSet.GetXml%2A>メソッドまたは<xref:System.Data.DataSet.WriteXml%2A>のメソッド、<xref:System.Data.DataSet>します。  
  
 呼び出す、<xref:System.Data.DataSet.GetXml%2A>メソッドは XML として書式設定するデータセット内のすべてのデータ テーブルからデータを含む文字列を返します。  
  
 呼び出す、<xref:System.Data.DataSet.WriteXml%2A>メソッドは、指定したファイルに XML 形式のデータを送信します。  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>データセット内の変数に XML としてデータを保存するには  
  
-   <xref:System.Data.DataSet.GetXml%2A>メソッドが返す、<xref:System.String>します。これは、型の変数を宣言することは意味<xref:System.String>の結果を割り当てると、<xref:System.Data.DataSet.GetXml%2A>メソッド。  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>データセット内のデータをファイルに XML として保存するには  
  
-   <xref:System.Data.DataSet.WriteXml%2A>メソッドが複数のオーバー ロードします。 次のコードでは、データをファイルに保存する方法を示します。変数を宣言し、ファイルを保存する有効なパスを割り当てます。  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>関連項目  
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)

