---
title: および型指定されていないデータセットの入力
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e5819a208a54a5a4235330216e46b5e17f1260fa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="typed-vs-untyped-datasets"></a>および型指定されていないデータセットの入力
型指定されたデータセットは、最初から派生した基本<xref:System.Data.DataSet>クラスおよびから情報を使用して、**データセット デザイナー**、厳密に型指定されたデータセット クラスは、新しいを生成する、.xsd ファイルに格納されています。 (テーブル、列、およびなど) のスキーマから情報が生成され、最上位のオブジェクトとプロパティのセットとしてこの新しい dataset クラスにコンパイルします。 指定されたデータセットは、ベースから継承するため<xref:System.Data.DataSet>クラス、型指定されたクラスのすべての機能の想定、<xref:System.Data.DataSet>クラスし、のインスタンスを取るメソッドで使用できる、<xref:System.Data.DataSet>クラスをパラメーターとして。

 これに対し、型指定されていない、データセットには対応する組み込みのスキーマがありません。 型指定されたデータセットと同様に、型指定されていないデータセットには、テーブルや列などが含まれています — コレクションとしてのみ公開されるものですが。 (ただし、型指定されていないデータセット内のテーブルおよびその他のデータ要素を手動で作成した後できる構造をエクスポートするデータセットのスキーマとして、データセットを使用して<xref:System.Data.DataSet.WriteXmlSchema%2A>メソッドです)。

## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>型指定された、型指定されていないデータセットのデータ アクセスの比較
 指定されたデータセットのクラスには、そのプロパティがテーブルと列の実際の名前で実行するオブジェクト モデルがあります。 たとえば、型指定されたデータセットで作業している場合は、次のようなコードを使用して列を参照できます。

 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

 これに対し、型指定されていないデータセットで作業している場合、同等のコードに示します。

 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

 型指定されたアクセスだけではなく、簡単に理解しますが、IntelliSense によって完全にサポートされても、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **コード エディター**です。 だけでなくを容易に操作は、型指定されたデータセットの構文は、データセットのメンバーに値を割り当てるときにエラーの可能性を大幅に軽減データ型は、コンパイル時にチェックを提供します。 内の列の名前を変更する場合、<xref:System.Data.DataSet>クラスおよびアプリケーションをコンパイルし、ビルド エラーが発生します。 内のビルド エラーをダブルクリックして、**タスク一覧**、古い列名を参照するコードの行に直接移動することができます。 型指定されたテーブルと列へのアクセス データセットは、アクセスが実行時にコレクションではなく、コンパイル時に決定されるためにも実行時に多少高速です。

 型指定されたデータセットでは、多くの利点がある、でも、型指定されていないデータセットはさまざまな状況で役立ちます。 最も明白なシナリオのデータセットの使用可能なスキーマがない場合です。 これが発生するなど、アプリケーションが、データセットを返すコンポーネントと対話する場合がわからない事前にその構造とは何です。 同様に、静的、予測可能な構造がないデータを使用している場合もあります。 その場合は、現実的ではない型指定されたデータセットを使用するため、型指定されたデータセット クラスをデータ構造の変更のたびに再生成する必要があります。

 一般的が何度も使用可能なスキーマをしなくても動的にデータセットを作成する場合があります。 その場合は、データセットは、データをリレーショナル方法で表現できる限り、情報を保持している便利な構造です。 同時に、別のプロセスに渡す、または XML ファイルを書き込む情報をシリアル化する機能などのデータセットの機能を活用を実行できます。

## <a name="see-also"></a>関連項目

- [データセットのツール](../data-tools/dataset-tools-in-visual-studio.md)