---
title: Manage.visualstudio.com または VLSC からサブスクリプションの割り当てメールを再送信する方法 | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 02/13/2018
ms.topic: Get-Started-Article
description: manage.visualstudio.com または VLSC からサブスクリプションの割り当てメールを再送信する方法について学習します
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 080ec95c73ed649168838d823a0dcc5d809ee89a
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="how-to-resend-subscription-assignment-emails-in-the-visual-studio-subscription-management-portal"></a>Visual Studio のサブスクリプション管理ポータルからサブスクリプションの割り当てメールを再送信する方法

割り当てメールの再送信に必要な手順は、サブスクリプションを管理するために使用するポータルによって異なります。 

## <a name="resending-assignment-emails-from-within-managevisualstudiocom"></a>manage.visualstudio.com 内からの割り当てメールの再送信

manage.visualstudio.com ポータル内から割り当てメールを再送信するためのプロセスは非常に簡単です。

1. [manage.visualstudio.com](https://manage.visualstudio.com) ポータルにアクセスしてサインインします。 
2. **[フィルター]** タブを使用して、割り当てメールを再送信するサブスクライバーを検索します  (フィルター処理の詳細については、[サブスクリプションの検索](/visualstudio/subscriptions/search-license)に関するページを参照してください)。
3. [サブスクリプション] タブをクリックします。  複数のサブスクライバーを選択するには、Ctrl キーを押しながらクリックするか、Shift キーを押しながらクリックします。
4. 検索結果の先頭にある**[再送信]** をクリックします。  

## <a name="resending-assignment-emails-from-within-vlsc"></a>VLSC 内からの割り当てメールの再送信
サブスクリプションが VLSC でサブスクライバーに割り当てられ、そのサブスクライバーから割り当てメールの再送信が要求された場合、サブスクライバーの電子メール情報を編集してから元のアドレスに戻すことで、これを行うことができます。 これにより割り当てメールの再送信が自動的にトリガーされます。

次の指示に従って、割り当てメールを再送信します。


1. ボリューム ライセンス サービス センター (VLSC) にアクセスしてサインインします。
2. VLSC の管理ページから、**[サブスクリプション]**、**[Visual Studio サブスクリプション]** の順にクリックします。
3. Visual Studio サブスクリプションに関連付けられている**契約番号**をクリックします。
4. **検索**バーで下矢印をクリックします。  
5. [電子メール アドレス] フィールドを使用してサブスクライバーを検索します。
6. 結果リストからサブスクライバーの**姓**をクリックします。
7. **[編集]** をクリックします。
8. サブスクリプションを編集します。 単に変更する必要があるだけなので、変更内容は何でもかまいません。  たとえば、サブスクライバーの電子メール アドレスの .com から "m" を 1 文字削除します。**[保存]** ボタンをクリックします。
9. 情報が保存されたら、**[編集]** ボタンをもう一度クリックして、電子メールから欠落している文字を修正します。 **[保存]**をクリックします。
   
これにより、サブスクリプションに変更があったことを VLSC に認識させ、割り当てメールがポータルにリストされている電子メールに再送信されます。 

> [!NOTE]
> - 新しく割り当てられたサブスクリプションは、割り当てメールを自動的に生成します。 上記は、ユーザーが新しい割り当てメールを要求した場合、または何らかの理由で通知が送信されない場合にのみ必要です。
