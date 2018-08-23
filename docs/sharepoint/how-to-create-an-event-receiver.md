---
title: '方法: イベント レシーバーの作成 |Microsoft Docs'
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
ms.openlocfilehash: dd4528a47215254684be51400329b05c3998bbab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "42635149"
---
# <a name="how-to-create-an-event-receiver"></a>方法: イベント レシーバーを作成
  作成して*イベント レシーバー*、リストなどの SharePoint アイテムまたはリスト項目と、ユーザーが対話するときに応答することができます。 たとえば、ユーザーがカレンダーを変更したり、連絡先リストから名前を削除、イベント レシーバー内でコードをトリガーできます。 このトピックでは、リスト インスタンスには、イベント レシーバーを追加する方法を確認できます。

 次の手順を完了する必要がありますインストールした[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]サポート対象エディションの Windows および SharePoint とします。 この例では、SharePoint プロジェクトが必要とするためもする必要がありますの手順を完了、トピックの「[チュートリアル: SharePoint のサイト列、コンテンツの種類、および一覧を作成する](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)します。

## <a name="adding-an-event-receiver"></a>イベント レシーバーの追加
 作成したプロジェクト[チュートリアル: SharePoint のサイト列、コンテンツの種類、および一覧を作成する](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)カスタムのサイト列、カスタム リスト、およびコンテンツの種類が含まれています。 次の手順では、リストなどの SharePoint アイテムで発生するイベントを処理する方法を表示するリスト インスタンスに単純なイベント ハンドラー (イベント レシーバー) を追加することでこのプロジェクトを展開します。

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>リスト インスタンスには、イベント レシーバーを追加するには

1.  作成したプロジェクトを開く[チュートリアル: SharePoint のサイト列、コンテンツの種類、および一覧を作成する](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)します。

2.  **ソリューション エクスプ ローラー**、名前は、SharePoint プロジェクト ノードを選択**クリニック**します。

3.  メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。

4.  いずれかで**Visual c#** または**Visual Basic**、展開、 **SharePoint**ノードを選択し、 **2010**項目。

5.  **テンプレート**ウィンドウで、選択**イベント レシーバー**、名前を付けます**TestEventReceiver1**、選択し、 **[ok]** ボタンをクリックします。

     **SharePoint カスタマイズ ウィザード**が表示されます。

6.  **イベント レシーバーの種類が必要ですか?** 一覧で、選択**リスト項目イベント**します。

7.  **どの項目がイベント ソースにする必要がありますか?** 一覧で、選択**患者 (Clinic\Patients)** します。

8.  **、次のイベントを処理**一覧で、次のチェック ボックスをオン**項目が追加されました**、選択し、**完了**ボタンをクリックします。

     新しいイベント レシーバーのコード ファイルには名前は 1 つのメソッドが含まれています`ItemAdded`します。 次の手順ですべての連絡先の名前は Scott Brown 既定するために、このメソッドにコードを追加します。

9. 既存`ItemAdded`メソッドを次のコードは、クリックして、 **F5**キー。

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     コードを実行し、SharePoint サイト、web ブラウザーに表示されます。

10. クイック起動バーで、**患者**リンクをクリックして、**新しい項目の追加**リンク。

     新しい項目のエントリ フォームが開きます。

11. フィールドに、データを入力してから、**保存**ボタンをクリックします。

     選択した後、**保存** ボタン、**患者名**Scott Brown 名に列が自動的に更新します。

## <a name="see-also"></a>関連項目

- [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)