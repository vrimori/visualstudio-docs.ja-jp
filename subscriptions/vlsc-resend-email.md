---
title: "Visual Studio のサブスクリプション: VLSC からの割り当てメールの再送"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend subscription assignment emails from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 338ae08ee1f3e6a819a1faea7bd095c9acd8ecd2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-within-volume-license-service-center-vlsc"></a>ボリューム ライセンス サービス センター (VLSC) からのサブスクリプションの割り当てメールの再送方法

サブスクリプションが割り当てられているサブスクライバーから、管理者にサブスクリプションの割り当てメールの再送依頼があることがあります。  これは、新しいサブスクリプションの管理ポータル (https://manage.visualstudio.com) で、簡単に実行できます。  ただし、組織がまだボリューム ライセンス サービス センター (VLSC) を使用している場合、通知メールを自動再送する機能はありません。  

VLSC 内から割り当てメールを再送するには、管理者は、次の解決策を実行する必要があります。

## <a name="resending-the-assignment-email"></a>割り当てメールの再送:

VLSC から新しい通知を生成するには、サブスクライバーのメール情報を 1 回を編集し、同じトランザクションで、元のメールに戻します。 これによって、VLSC は、新しいサブスクリプションが割り当てられたのと同じ動作をし、割り当てメールを再送します。

1.  [ボリューム ライセンス サービス センター (VLSC) ](https://www.microsoft.com/Licensing/servicecenter/default.aspx)にアクセスしてサインインします。
2.  **[サブスクリプション]** タブをクリックして、**[Visual Studio サブスクリプション]** を選びます。
3.  Visual Studio サブスクリプションに関連付けられている**契約番号**をクリックします。
4.  検索バーで下矢印をクリックします。 
5.  **[電子メール アドレス]** フィールドを使用してサブスクライバーを検索します。
6.  検索結果でサブスクライバーを見つけて、姓をクリックします。 
7.  **[編集]** をクリックします。
8.  サブスクリプションを編集します。 たとえば、サブスクライバーの電子メール アドレスから文字を削除します。 **[保存]** ボタンをクリックします。
9.  情報を保存したら、再度 **[編集]** をクリックして、行った変更を元に戻して **[保存]** をクリックします。  

これにより、サブスクリプションは新しい割り当てとして扱われ、サブスクライバーに割り当てメールが再送されます。  