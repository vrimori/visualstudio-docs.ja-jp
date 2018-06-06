---
title: 管理者ポータルでのサブスクリプションの編集 | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: 管理者がサブスクリプションの割り当てを編集する方法を説明します。
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: e4ee209af97d09f5d7e2125d2111746f6fe491f5
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34476639"
---
# <a name="editing-visual-studio-subscription-assignments"></a>Visual Studio サブスクリプションの割り当ての編集

サブスクリプション管理者は、組織内の個人に割り当てられているサブスクリプションに変更を加えることができます。  この記事では、行うことができる変更の種類と、必要な手順について説明します。 

## <a name="making-changes-to-subscriber-information"></a>サブスクライバー情報を変更する
サブスクライバー情報を編集してエラーを修正したり情報を更新したりすることができます。 

サブスクライバーを編集するには、サブスクライバーの電子メール アドレスの横にマウス ポインターを移動すると表示される省略記号 (...) を選択します。 ドロップダウン リストが表示されます。  **[編集]** を選択して、サブスクライバーの詳細を変更します。 グリッドのサブスクライバーの行をダブルクリックして編集ウィンドウを開くこともできます。

   <img alt="Select subscriber to edit" src="_img\edit-license\select-subscriber.png" style="border: 1px solid #CCCCCC" />
    
サブスクライバーの名、姓、国、言語およびダウンロードを更新することができます。 サブスクライバーの情報を編集し、**[保存]** をクリックします。

 
   <img alt="Edit subscriber details" src="_img\edit-license\edit-subscriber.png" style="border: 1px solid #CCCCCC" />
   > [!NOTE]
   > サブスクライバーのサブスクリプション レベルを変更する必要がある場合、ポータルからユーザーを削除し、もう一度追加する必要があります。 サブスクリプション レベルは編集できません。

## <a name="editing-multiple-subscribers-by-using-bulk-edit"></a>一括編集を使用して複数のサブスクライバーを編集する

一括編集プロセスを使用して、一度に複数のサブスクライバーを編集することができます。 この機能は、会社の電子メール アドレスを変更している組織、または組織がダウンロードへのアクセスを制限することにした場合に主に使用されます。 

   > [!IMPORTANT]
   > サブスクリプション レベル (つまり Enterprise や Professional など) とサブスクリプションの GUID を変更することはできません。  変更されたこれらの項目をアップロードする場合、アップロードは失敗します。  

1.  複数のサブスクライバーを一度に追加するには、[サブスクライバー] タブに移動します。上部リボンの **[一括編集]** をクリックします。 

    <img alt="Editing a License - Bulk Edits" src="_img\edit-license\edit-license-bulk-edit.png" style="border: 1px solid #CCCCCC" />

2.  一括編集では、Excel テンプレートを使用してサブスクライバー情報を編集します。 一括編集ボックスで、**[Excel にエクスポート]** をクリックして、すべての情報を含む現在のサブスクライバーの一覧をダウンロードします。 

    <img alt="Editing a License - Export Bulk Edits List" src="_img\edit-license\edit-license-bulk-edit-export.png" style="border: 1px solid #CCCCCC" />

3.  次に、アップロードする前に簡単に見つけて必要な変更を行うことができるように、ファイルをローカルに保存します。 アップロードを成功させるには、**サブスクリプション レベルまたはサブスクリプションの GUID を編集しないでください**。そのようにするとアップロードが失敗します。 

4.  Visual Studio サブスクリプション管理ポータルに戻り、[一括編集] ダイアログ ボックスで **[参照]** をクリックします。 保存した Excel ファイルを選んで、**[OK]** をクリックします。 アップロードの進行状況が画面に表示されます。

    <img alt="Editing a License - Bulk Edits File Upload" src="_img\edit-license\edit-license-bulk-file-upload1.png" style="border: 1px solid #CCCCCC" />

5.  ファイルをアップロードしたら、成功したことを知らせる通知が表示されます。 この時点で、編集内容がサブスクライバーの情報に反映されます。 

    <img alt="Editing a License - Bulk Edits Upload Complete" src="_img\edit-license\edit-license-bulk-upload-complete.png" style="border: 1px solid #CCCCCC" />

