---
title: 型指定されていないデータセットと型指定された |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 287a0ceae792a91e676982f5ec47d3905966956b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538314"
---
# <a name="typed-vs-untyped-datasets"></a>型指定されたデータセットと型指定されていないデータセットの比較
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[型指定されていないデータセットと型指定された](https://docs.microsoft.com/visualstudio/data-tools/typed-vs-untyped-datasets)します。  
  
  
型指定されたデータセットはまず、ベースから派生したデータセット<xref:System.Data.DataSet>クラスし、からの情報を使用して、**データセット デザイナー**、厳密に型指定された dataset クラスを新しいを生成する、.xsd ファイルに格納されています。 (テーブル、列、およびなど) のスキーマから情報が生成され、最上位のオブジェクトとプロパティのセットとして、この新しい dataset クラスにコンパイルします。 型指定されたデータセットは、ベースから継承するため<xref:System.Data.DataSet>クラス、型指定されたクラスはすべての機能の<xref:System.Data.DataSet>クラスし、のインスタンスを取るメソッドで使用できる、<xref:System.Data.DataSet>クラスをパラメーターとして。  
  
 これに対し、型指定されていないデータセットには対応する組み込みのスキーマがありません。 型指定されたデータセットのように、データセットには、テーブルや列などが含まれています — はコレクションとしてのみ公開されるものが、します。 (ただし、データセットのテーブルとその他のデータ要素を手動で作成した後できます構造をエクスポートするデータセットのスキーマとして、データセットを使用して<xref:System.Data.DataSet.WriteXmlSchema%2A>メソッドです)。  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>型指定された、型指定されていないデータセットのデータ アクセスの比較  
 型指定されたデータセットのクラスには、テーブルと列の実際の名前でそのプロパティを使用する、オブジェクト モデルがあります。 たとえば、型指定されたデータセットを使用する場合、次のコードを使用して列を参照できます。  
  
 [!code-csharp[VbRaddataDatasets#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#4)]
 [!code-vb[VbRaddataDatasets#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#4)]  
  
 これに対し、データセットを使用する場合、同等のコードには。  
  
 [!code-csharp[VbRaddataDatasets#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#5)]
 [!code-vb[VbRaddataDatasets#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#5)]  
  
 型指定されたアクセスはだけでなく、読みやすくが IntelliSense によっても完全にサポートされる、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **コード エディター**します。 簡単に扱うだけは、型指定されたデータセットの構文は、型、コンパイル時チェックのデータセットのメンバーに値を割り当てるときにエラーの可能性を大幅に削減を提供します。 内の列の名前を変更する場合、<xref:System.Data.DataSet>クラスし、アプリケーションをコンパイルし、ビルド エラーが発生します。 内のビルド エラーをダブルクリックして、**タスク一覧**、古い列名を参照するコードの行に直接移動することができます。 型指定されたテーブルと列へのアクセス データセットは、アクセスは、実行時にコレクションではなく、コンパイル時に決定されるためにも実行時に多少高速です。  
  
 型指定されたデータセットでは、多くの利点がある、でも、型指定されていないデータセットがさまざまな状況で役に立ちます。 最も明白なシナリオでは、データセットのスキーマがない場合です。 これが発生するなど、アプリケーションが、データセットを返すコンポーネントと対話する場合が、不明な事前にその構造とは何です。 同様に、静的で予測可能な構造がないデータを使用する場合もあります。 その場合は、ことはできません型指定されたデータセットを使用するは実用的データ構造のそれぞれの変更を使用して、型指定されたデータセット クラスを再生成する必要があります。  
  
 一般的が何度も使用可能なスキーマをしなくても、データセットを動的に作成する場合があります。 その場合は、データセットは、リレーショナルの方法でデータを表現できる限り、情報を保持している便利な構造です。 同時に、別のプロセスに渡す、または XML ファイルを記述する情報をシリアル化する機能などのデータセットの機能を活用を実行できます。

