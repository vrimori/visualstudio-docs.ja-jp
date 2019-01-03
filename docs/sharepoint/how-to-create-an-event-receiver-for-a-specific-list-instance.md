---
title: '方法: 特定のリスト インスタンスに対するイベント レシーバーを作成 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a92b86d7e02487ff333fb8517086f9c6221d35ec
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53818863"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>方法: 特定のリスト インスタンスに対するイベント レシーバーを作成します。
  リスト インスタンスのイベント レシーバーは、リスト定義の任意のインスタンスで発生するイベントに応答します。 イベント レシーバーのテンプレートでは、特定のリスト インスタンスのターゲットを有効にはない、特定のリスト インスタンス内のイベントに応答するリスト定義のスコープをイベント レシーバーを変更できます。  
  
 特定のリスト インスタンスを対象に、 *Elements.xml* 、イベント レシーバー置換`ListTemplateId`で`ListUrl`リスト インスタンスの URL を追加します。  
  
## <a name="create-a-list-instance-event-receiver"></a>リスト インスタンスのイベント レシーバーを作成します。  
 次の手順では、カスタムのお知らせリスト インスタンスで発生するイベントのみに対応するリスト項目イベント レシーバーを変更する方法を紹介します。  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>特定のリスト インスタンスに応答するイベント レシーバーを変更するには  
  
1.  ブラウザーで SharePoint サイトを開きます。  
  
2.  ナビゲーション ウィンドウで**一覧**リンク。  
  
3.  **すべてのサイト コンテンツ**ページで、選択、**作成**リンク。  
  
4.  **作成** ダイアログ ボックスで、選択、**お知らせ**型、お知らせを名前**TestAnnouncements**、選択し、**作成**ボタンをクリックします。  
  
5.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、イベント レシーバー プロジェクトを作成します。  
  
6.  **イベント レシーバーの種類が必要ですか?** 一覧で、選択**リスト項目イベント**します。  
  
    > [!NOTE]  
    >  たとえば、リスト定義をスコープとなるイベント レシーバーの他の種類を選択することも**リスト電子メール イベント**または**リスト ワークフロー イベント**します。  
  
7.  **どの項目がイベント ソースにする必要がありますか?** 一覧で、選択**お知らせ**します。  
  
8.  **、次のイベントを処理**一覧で、、**項目が追加されている**チェック ボックスをオンにして、**完了**ボタンをクリックします。  
  
9. **ソリューション エクスプ ローラー**、EventReceiver1、開く*Elements.xml*します。  
  
     現在、イベント レシーバーは、次の行を使用してお知らせリストの定義を参照します。  
  
    ```xml  
    <Receivers ListTemplateId="104">  
    ```  
  
     次のテキストには、この行を変更します。  
  
    ```xml  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     これにより、新しいで発生するイベントにのみ応答するイベント レシーバー **TestAnnouncements**作成したお知らせリスト。 変更することができます、 `ListURL` SharePoint サーバーのリスト インスタンスを参照する属性。  
  
10. イベント レシーバーのコード ファイルを開き、ItemAdding メソッドにブレークポイントを設定します。  
  
11. 選択、 **F5**キー、ソリューションをビルドして実行します。  
  
12. SharePoint では、選択、 **TestAnnouncements**ナビゲーション ウィンドウでリンクします。  
  
13. 選択、**新しいお知らせの追加**リンク。  
  
14. お知らせのタイトルを入力し、、**保存**ボタンをクリックします。  
  
     カスタムお知らせリストに新しい項目が追加されたときにブレークポイントがヒットしたことに注意してください。  
  
15. 選択、 **F5**を再開するキー。  
  
16. ナビゲーション ウィンドウで選択、**を一覧表示**リンクをクリックして、**お知らせ**リンク。  
  
17. 新しいお知らせを追加します。  
  
     イベント レシーバーでは、カスタム アナウンス リスト インスタンス内のイベントにのみ応答する、受信側が構成されているために、新しいお知らせをトリガーしません通知**TestAnnouncements**します。  
  
## <a name="see-also"></a>関連項目
 [方法: イベント レシーバーを作成します。](../sharepoint/how-to-create-an-event-receiver.md)   
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
