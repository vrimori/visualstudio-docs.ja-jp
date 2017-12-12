---
title: "管理者ポータルでサブスクリプションを編集する | Visual Studio Marketplace"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: "管理者がサブスクリプションの割り当てを編集する方法を説明します。"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 985dea7a301130d4641ef9ba3ca2c5ae67218ad4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="editing-visual-studio-subscription-assignments"></a>Visual Studio サブスクリプションの割り当ての編集

## <a name="making-changes-to-subscriber-information"></a>サブスクライバー情報を変更する
サブスクライバー情報を編集してエラーを修正したり情報を更新したりすることができます。 
**サブスクライバーの電子メール アドレスの編集により、既存の特典がリセットされることに注意してください。**

サブスクライバーを編集するには、サブスクライバーの電子メール アドレスの横にマウス ポインターを移動すると表示される省略記号 (...) を選択します。 ドロップダウン リストが表示されます。  **[編集]** を選択して、サブスクライバーの詳細を変更します。 グリッドのサブスクライバーの行をダブルクリックして編集ウィンドウを開くこともできます。

![編集するサブスクライバーを選択する](_img\edit-license\select-subscriber.png)

サブスクライバーの名、姓、国、言語およびダウンロードを更新することができます。 サブスクライバーの情報を編集し、**[保存]** をクリックします。

![サブスクライバーの詳細の編集](_img\edit-license\edit-subscriber.png)

注: サブスクライバーのサブスクリプション レベルを変更する必要がある場合、ポータルからユーザーを削除し、もう一度追加する必要があります。 サブスクリプション レベルは編集できません。

## <a name="editing-multiple-subscribers-by-using-bulk-edit"></a>一括編集を使用して複数のサブスクライバーを編集する

一括編集プロセスを使用して、一度に複数のサブスクライバーを編集することができます。 この機能は、会社の電子メール アドレスを変更している組織、または組織がダウンロードへのアクセスを制限することにした場合に主に使用されます。 **重要:** サブスクリプション レベル (つまり Enterprise や Professional など) とサブスクリプションの GUID を変更することはできません。  変更されたこれらの項目をアップロードする場合、アップロードは失敗します。  

1.  複数のサブスクライバーを一度に追加するには、[サブスクライバー] タブに移動します。上部リボンの **[一括編集]** をクリックします。 

![ライセンスの編集 - 一括集](_img\edit-license\edit-license-bulk-edit.png)

2.  一括編集では、Excel テンプレートを使用してサブスクライバー情報を編集します。 一括編集ボックスで、**[Excel にエクスポート]** をクリックして、すべての情報を含む現在のサブスクライバーの一覧をダウンロードします。 

![ライセンスの編集 - 一括編集一覧のエクスポート](_img\edit-license\edit-license-bulk-edit-export.png)

3.  次に、アップロードする前に簡単に見つけて必要な変更を行うことができるように、ファイルをローカルに保存します。 アップロードを成功させるには、**サブスクリプション レベルまたはサブスクリプションの GUID を編集しないでください**。そのようにするとアップロードが失敗します。 

4.  Visual Studio サブスクリプション管理ポータルに戻り、[一括編集] ダイアログ ボックスで **[参照]** をクリックします。 保存した Excel ファイルを選んで、**[OK]** をクリックします。 アップロードの進行状況が画面に表示されます。

![ライセンスの編集 - 一括編集のファイルのアップロード](_img\edit-license\edit-license-bulk-file-upload.png)

5.  ファイルをアップロードしたら、成功したことを知らせる通知が表示されます。 

![ライセンスの編集 - 一括編集のアップロードの完了](_img\edit-license\edit-license-bulk-upload-complete.png)


