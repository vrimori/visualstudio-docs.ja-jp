---
title: "方法: 特定のリスト インスタンスのイベント レシーバーを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a820bc1a29db10fa5f65f1781c30218c62c2ee08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>方法: 特定のリスト インスタンスに対するイベント レシーバーを作成する
  リスト インスタンスのイベント レシーバーは、リスト定義の任意のインスタンスで発生するイベントに応答します。 イベント レシーバーのテンプレートでは、特定のリスト インスタンスのターゲット設定は有効にしません、対象とする特定のリスト インスタンス内のイベントに応答するリストの定義には、イベント レシーバーを変更することができます。  
  
 イベント レシーバーを Elements.xml での特定のリスト インスタンスを対象に置き換える`ListTemplateId`で`ListUrl`し、リスト インスタンスの URL を追加します。  
  
## <a name="creating-a-list-instance-event-receiver"></a>リスト インスタンス イベント レシーバーを作成します。  
 次の手順では、カスタムのお知らせリスト インスタンスで発生するイベントにのみ応答するには、リスト アイテム イベント レシーバーを変更する方法を示します。  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>特定のリスト インスタンスに応答するイベント レシーバーを変更するには  
  
1.  ブラウザーで SharePoint サイトを開きます。  
  
2.  ナビゲーション ウィンドウで、**一覧**リンクします。  
  
3.  **すべてのサイト コンテンツ**ページで、選択、**作成**リンクします。  
  
4.  **作成** ダイアログ ボックスで、選択、**お知らせ**型、お知らせを名前**TestAnnouncements**を選択し、**作成**ボタンをクリックします。  
  
5.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、イベント レシーバー プロジェクトを作成します。  
  
6.  **イベント レシーバーの種類が必要ですか?**一覧で、選択**リスト項目イベント**です。  
  
    > [!NOTE]  
    >  その他の種類のリストの定義に、スコープのイベント レシーバーを選択することもできます。**リスト電子メール イベント**または**リスト ワークフロー イベント**です。  
  
7.  **イベント ソースとなる項目?**一覧で、選択**お知らせ**です。  
  
8.  **、次のイベントを処理**一覧で、、**項目が追加されている**チェック ボックスをオンにして、**完了**ボタンをクリックします。  
  
9. **ソリューション エクスプ ローラー**EventReceiver1、下にある Elements.xml を開きます。  
  
     イベント レシーバーは、現在次の行を使用してお知らせリストの定義を参照します。  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     この行を次のテキストに変更します。  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     これにより、新しいで発生するイベントにのみ応答するイベント レシーバー **TestAnnouncements**先ほど作成したお知らせリスト。 変更することができます、 `ListURL` SharePoint サーバー上の任意のリスト インスタンスを参照する属性。  
  
10. イベント レシーバーにコード ファイルを開き、ItemAdding メソッドにブレークポイントを設定します。  
  
11. F5 キーをソリューションをビルドおよび実行を選択します。  
  
12. SharePoint では、選択、 **TestAnnouncements**ナビゲーション ウィンドウでリンクします。  
  
13. 選択、**新しいお知らせの追加**リンクします。  
  
14. 発表については、タイトルを入力し、、**保存**ボタンをクリックします。  
  
     カスタムのお知らせリストに新しい項目が追加されたときに、ブレークポイントにヒットすることに注意してください。  
  
15. 再開する、F5 キーを選択します。  
  
16. ナビゲーション ウィンドウで、選択、**を一覧表示**リンクをクリックして、**お知らせ**リンクします。  
  
17. 新しいお知らせを追加します。  
  
     イベント レシーバーでは、カスタム アナウンス リスト インスタンス内のイベントにのみ応答する、受信者が構成されているために、新しいお知らせで発生しません通知**TestAnnouncements**です。  
  
## <a name="see-also"></a>参照  
 [方法: イベント レシーバーを作成します。](../sharepoint/how-to-create-an-event-receiver.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  