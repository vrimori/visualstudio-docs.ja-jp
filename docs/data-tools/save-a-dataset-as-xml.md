---
title: データセットを XML として保存する
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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5a1b0c453f3b48b12c5a77fce86789a66fe77c26
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173998"
---
# <a name="save-a-dataset-as-xml"></a>データセットを XML として保存する

データセットで使用可能な XML メソッドを呼び出すことにより、データセット内の XML データにアクセスします。 XML 形式でデータを保存する、いずれかを呼び出すことができます、<xref:System.Data.DataSet.GetXml%2A>メソッドまたは<xref:System.Data.DataSet.WriteXml%2A>のメソッド、<xref:System.Data.DataSet>します。

呼び出す、<xref:System.Data.DataSet.GetXml%2A>メソッドは XML として書式設定するデータセット内のすべてのデータ テーブルからデータを含む文字列を返します。

呼び出す、<xref:System.Data.DataSet.WriteXml%2A>メソッドは、指定したファイルに XML 形式のデータを送信します。

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>データセット内の変数に XML としてデータを保存するには

- <xref:System.Data.DataSet.GetXml%2A>メソッドが返す、<xref:System.String>します。 型の変数を宣言<xref:System.String>の結果を割り当てると、<xref:System.Data.DataSet.GetXml%2A>メソッド。

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>データセット内のデータをファイルに XML として保存するには

- <xref:System.Data.DataSet.WriteXml%2A>メソッドが複数のオーバー ロードします。 変数を宣言し、ファイルを保存する有効なパスを割り当てます。 次のコードでは、データをファイルに保存する方法を示します。

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)