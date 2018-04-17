---
title: '方法: 追加、更新、または WCF データ サービス参照の削除 |Microsoft ドキュメント'
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2e128268a0dd81aead3204436bb8f4ea80b5a048
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>方法: WCF データ サービス参照を追加、更新、または削除する
A*サービス リファレンス*によって、プロジェクトで 1 つまたは複数のアクセスを[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]です。 使用して、**サービス参照の追加**を検索 ダイアログ ボックス[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]ローカル、ローカル エリア ネットワーク、またはインターネット上の現在のソリューションにします。  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="adding-a-service-reference"></a>サービス参照の追加  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>外部サービスへの参照を追加するには  
  
1.  **ソリューション エクスプ ローラー**、クリックして、サービスを追加するプロジェクトの名前を右クリックして**サービス参照の追加**です。  
  
     **サービス参照の追加** ダイアログ ボックスが表示されます。  
  
2.  **アドレス**ボックスで、サービスの URL を入力し、をクリックして**移動**サービスを検索します。 サービスは、ユーザー名とパスワードのセキュリティを実装する場合、ユーザー名とパスワードを求めるメッセージが表示します。  
  
    > [!NOTE]
    >  信頼できるソースのサービスのみを参照してください。 信頼できないソースの参照を追加すると、セキュリティが損なわれる可能性があります。  
  
     URL を選択することも、**アドレス**一覧で、有効なサービスのメタデータを検出する位置を前の 15 の Url を格納します。  
  
     検索の実行中は進行状況バーが表示されます。 クリックして、いつでも検索を停止できます**停止**です。  
  
3.  **Services**一覧で、使用して、エンティティ セットを選択するサービスのノードを展開します。  
  
4.  **Namespace**ボックスで、参照に使用する名前空間を入力します。  
  
5.  をクリックして**OK**プロジェクトに参照を追加します。  
  
     サービス クライアント (プロキシ) が生成され、サービスを記述したメタデータが app.config ファイルに追加します。  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>現在のソリューションに、サービスへの参照を追加するには  
  
1.  **ソリューション エクスプ ローラー**、クリックして、サービスを追加するプロジェクトの名前を右クリックして**サービス参照の追加**です。  
  
     **サービス参照の追加** ダイアログ ボックスが表示されます。  
  
2.  をクリックして**検出**です。  
  
     すべてのサービス (両方[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]および WCF サービス) で、現在のソリューションに追加されます、 **Services**  ボックスの一覧です。  
  
3.  **Services**一覧で、使用して、エンティティ セットを選択するサービスのノードを展開します。  
  
4.  **Namespace**ボックスで、参照に使用する名前空間を入力します。  
  
5.  をクリックして**OK**プロジェクトに参照を追加します。  
  
     サービス クライアント (プロキシ) が生成され、サービスを記述したメタデータが app.config ファイルに追加します。  
  
## <a name="updating-a-service-reference"></a>サービス参照の更新  
 エンティティ データ モデル、[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]が変わることがあります。 この場合、サービス参照を更新する必要があります。  
  
#### <a name="to-update-a-service-reference"></a>サービス参照を更新するには  
  
-   **ソリューション エクスプ ローラー**サービス参照を右クリックし、クリックして**サービス参照の更新**です。  
  
     元の場所から参照が更新され、メタデータの変更を反映して、サービス クライアントが再生成中に、進行状況 ダイアログ ボックスが表示されます。  
  
## <a name="removing-a-service-reference"></a>サービス参照の削除  
 サービス参照が使用されていないが場合、は、ソリューションから削除できます。  
  
#### <a name="to-remove-a-service-reference"></a>サービス参照を削除するには  
  
-   **ソリューション エクスプ ローラー**サービス参照を右クリックし、クリックして**削除**です。  
  
     サービス クライアントは、ソリューションから削除され、サービスを記述したメタデータが app.config ファイルから削除されます。  
  
    > [!NOTE]
    >  サービス参照を参照するすべてのコードは、手動で削除する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)