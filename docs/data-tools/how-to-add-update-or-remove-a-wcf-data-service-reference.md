---
title: '方法: WCF データ サービス参照を追加、更新、または削除する'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b6726b2c859143f5dbc9b264e67bb9bb91757de5
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089313"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>方法: 追加、更新、または WCF データ サービス参照の削除
A *service リファレンス*アクセスを 1 つまたは複数のプロジェクト[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]します。 使用して、**サービス参照の追加**を検索 ダイアログ ボックス[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]でローカルに、ローカル エリア ネットワーク、またはインターネット上の現在のソリューションです。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>サービス参照を追加します。

### <a name="to-add-a-reference-to-an-external-service"></a>外部サービスへの参照を追加するには

1.  **ソリューション エクスプ ローラー**をクリックして、サービスを追加するプロジェクトの名前を右クリックして**サービス参照の追加**します。

     **サービス参照の追加** ダイアログ ボックスが表示されます。

2.  **アドレス**ボックス、サービスの URL を入力して、クリックして**移動**サービスを検索します。 サービスは、ユーザー名とパスワードのセキュリティを実装する場合は、ユーザー名とパスワードを求める場合があります。

    > [!NOTE]
    >  信頼できるソースのサービスのみを参照してください。 信頼できないソースの参照を追加すると、セキュリティが損なわれる可能性があります。

     URL を選択することも、**アドレス**一覧で、有効なサービスのメタデータが見つかりましたが、以前の 15 Url が格納されます。

     検索の実行中は進行状況バーが表示されます。 クリックして、いつでも検索を停止する**停止**します。

3.  **サービス**一覧で、ノードを使用して、エンティティ セットを選択するサービスを展開します。

4.  **Namespace**ボックスに、参照で使用する名前空間を入力します。

5.  クリックして**OK**プロジェクトへの参照を追加します。

     サービス クライアント (プロキシ) が生成され、サービスを説明するメタデータに追加されます、 *app.config*ファイル。

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>現在のソリューションでサービスへの参照を追加するには

1.  **ソリューション エクスプ ローラー**をクリックして、サービスを追加するプロジェクトの名前を右クリックして**サービス参照の追加**します。

     **サービス参照の追加** ダイアログ ボックスが表示されます。

2.  クリックして**検出**します。

     すべてのサービス (両方[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]および WCF サービス) で、現在のソリューションに追加されます、**サービス**一覧。

3.  **サービス**一覧で、ノードを使用して、エンティティ セットを選択するサービスを展開します。

4.  **Namespace**ボックスに、参照で使用する名前空間を入力します。

5.  クリックして**OK**プロジェクトへの参照を追加します。

     サービス クライアント (プロキシ) を生成、およびサービスを記述したメタデータに追加されます、 *app.config*ファイル。

## <a name="update-a-service-reference"></a>サービス参照を更新します。
 エンティティ データ モデル、[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]場合があります。 この場合、サービス参照を更新する必要があります。

### <a name="to-update-a-service-reference"></a>サービス参照を更新するには

-   **ソリューション エクスプ ローラー**サービス参照を右クリックし、クリックして**サービス参照の更新**します。

     元の場所から、参照を更新し、メタデータの変更を反映する、サービス クライアントを再生成中に進行状況 ダイアログ ボックスを表示します。

## <a name="remove-a-service-reference"></a>サービス参照を削除します。
 サービス参照が使用されていないが場合、は、ソリューションから削除できます。

### <a name="to-remove-a-service-reference"></a>サービス参照を削除するには

-   **ソリューション エクスプ ローラー**サービス参照を右クリックし、クリックして**削除**します。

     サービス クライアントは、ソリューションから削除して、サービスを記述するメタデータはから削除されます、 *app.config*ファイル。

    > [!NOTE]
    >  サービス参照を参照するコードを手動で削除する必要があります。

## <a name="see-also"></a>関連項目

- [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)