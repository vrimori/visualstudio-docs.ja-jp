---
title: '方法: イベント レシーバーを作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: ead81e01022c8f389ad6010c89d0e433b82c542e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-event-receiver"></a>方法: イベント レシーバーを作成する
  作成することで*イベント レシーバー*、リストなどの SharePoint アイテムまたはリスト項目をユーザーが操作するときに応答することができます。 たとえば、ユーザーが、予定表を変更または連絡先のリストから名前を削除するときは、イベント レシーバーにコードをトリガーできます。 このトピックでは、リスト インスタンスをイベント レシーバーを追加する方法を学びます。  
  
 次の手順を完了する必要がありますインストールした[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]サポート対象エディションの Windows および SharePoint とします。 詳細については、次を参照してください。 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)です。 この例では、SharePoint プロジェクトが必要とするためも行うには、トピックの手順で[チュートリアル: サイト内の列、コンテンツ タイプ、および SharePoint のリストを作成する](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)です。  
  
## <a name="adding-an-event-receiver"></a>イベント レシーバーの追加  
 作成したプロジェクト[チュートリアル: SharePoint のサイト列、コンテンツの種類、およびリストを作成する](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)カスタムのサイト列、カスタム リスト、およびコンテンツの種類が含まれています。 次の手順では、リストなどの SharePoint アイテムで発生するイベントを処理する方法を表示するリスト インスタンスを単純なイベント ハンドラー (イベント レシーバー) を追加することでこのプロジェクトを展開します。  
  
#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>リスト インスタンスには、イベント レシーバーを追加するには  
  
1.  作成したプロジェクトを開く[チュートリアル: サイト内の列、コンテンツ タイプ、および SharePoint のリストを作成する](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)です。  
  
2.  **ソリューション エクスプ ローラー**を選択すると、SharePoint プロジェクト ノードの名前は**クリニック**です。  
  
3.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
4.  いずれかで**Visual c#**または**Visual Basic**、展開、 **SharePoint**  ノードを選択し、 **2010**項目。  
  
5.  **テンプレート** ウィンドウで、選択**イベント レシーバー**、名前を付けます**TestEventReceiver1**を選択し、 **ok**ボタンをクリックします。  
  
     **SharePoint カスタマイズ ウィザード**が表示されます。  
  
6.  **イベント レシーバーの種類が必要ですか?**一覧で、選択**リスト項目イベント**です。  
  
7.  **イベント ソースとなる項目?**一覧で、選択**患者 (Clinic\Patients)**です。  
  
8.  **、次のイベントを処理**一覧で、次のチェック ボックスをオン**項目が追加されました**を選択し、**完了**ボタンをクリックします。  
  
     新しいイベント レシーバーのコード ファイルには、名前は 1 つのメソッドが含まれています。`ItemAdded`です。 次の手順でを各連絡先の名前は Scott Brown 既定ようにこのメソッドにコードを追加します。  
  
9. 置き換えます`ItemAdded`メソッドに次のコードし、F5 キーを押します。  
  
     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     コードを実行し、SharePoint サイト、web ブラウザーに表示されます。  
  
10. クイック起動バーで、選択、**患者**リンクをクリックして、**新しい項目の追加**リンクします。  
  
     新しい項目のエントリ フォームが開きます。  
  
11. フィールドに、データを入力し、、**保存**ボタンをクリックします。  
  
     選択した後、**保存**ボタン、**患者名**名 Scott Brown に列が自動的に更新します。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
  