---
title: Visual Studio サブスクリプションにライセンスを割り当てる | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: 管理者がサブスクライバーにライセンスを割り当てる方法を説明します
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 4325921bbaa75e0fb8a8a16947c45901b6f01649
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34477380"
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Visual Studio サブスクリプション管理者ポータルでライセンスを割り当てる

Visual Studio サブスクリプションの管理者は、Visual Studio サブスクリプションの管理者ポータルを使用して、個々のユーザーにサブスクリプションを割り当てることができます。  
ユーザー 1 人ずつに割り当てることも、[一括追加] 機能を使用して迅速かつ簡単にサブスクリプション情報でサブスクライバーの一覧をアップロードすることも可能です。 

## <a name="assigning-a-single-user"></a>1 人のユーザーの割り当て
Visual Studio サブスクリプションに利用可能なライセンスがある場合は、新しいユーザーにそのライセンスを割り当てて、サブスクリプションの特典にアクセスできるようにすることができます。 
1.  [管理者ポータル](https://manage.visualstudio.com)へのサインイン

2.  1 人の Visual Studio サブスクライバーを割り当てるには、テーブルの上部にある **[追加]** をクリックします。

    <img alt="Add subscriber" src="_img\assign-license-add\assign-license-add.png" style="border: 1px solid #CCCCCC" />

3.  フォームのフィールドに新しいサブスクライバーの情報を入力します。 組織が Azure Active Directory を使っている場合は、このフィールドを使って現在のディレクトリのユーザーを検索し、検索結果から適切なユーザーを選ぶことができます。 ユーザーを選ぶと、名前、サインイン メール アドレス、通知メール アドレスが自動的に設定されます (下図参照)。 

    組織が Azure Active Directory (Azure AD) を使用しておらず、メール受信用の電子メール アドレスがサインイン用と異なる場合は、ここで入力できます。 [Add a different email for receiving communication]\(連絡の受信用に別の通知電子メール アドレスを追加する\) というハイパーリンクを選択します。 

    **ダウロードへのアクセス:**  
    このサブスクライバーが [Visual Studio サブスクリプション ポータル](https://my.visualstudio.com?wt.mc_id=o~msft~docs)にサインインするときにソフトウェアのダウンロードにアクセスできるようにする場合は、必ず、ダウンロードのトグルをオンのままにしてください。 ダウンロードを無効にすると、ユーザーはソフトウェアのダウンロードにアクセスできなくなりますが、サブスクリプションに含まれる他のすべての特典には引き続きアクセスできます。 
    
    このサブスクライバーのオプション選択が完了したら、**[追加]** をクリックします。

    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-1.png" style="border: 1px solid #CCCCCC" />
    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-2.png" style="border: 1px solid #CCCCCC" />

4.  サブスクライバーを追加すると、詳細な説明が記載された割り当てメールがサブスクライバーに自動的に送信されます。 サブスクライバーを選択して、上部メニューの **[再送信]** ボタンをクリックすることで、いつでも割り当てメールを送信し直すことができます。

    <img alt="Subscriber added" src="_img\assign-license-add\add-subscriber-complete.png" style="border: 1px solid #CCCCCC" />

## <a name="bulk-assignments"></a>一括割り当て
1.  複数のサブスクライバーを一度に追加するには、**[サブスクライバーの管理]** タブに移動します。上部リボンの **[一括追加]** をクリックします。 

    <img alt="Bulk add" src="_img\assign-license-add\bulk-assign-add.png" style="border: 1px solid #CCCCCC" />

2. 一括割り当てでは、Microsoft Excel テンプレートを使ってサブスクライバーをアップロードします。 [Upload Multiple Subscribers]\(複数のサブスクライバーのアップロード\) ダイアログ ボックスで、**[ダウンロード]** をクリックしてテンプレートをダウンロードします。 常にこのテンプレートの最新バージョンをダウンロードしてください。 古いバージョンを使うと、一括アップロードが失敗する可能性があります。

    <img alt="Upload multiple subscribers" src="_img\assign-license-add\bulk-assign-upload.png" style="border: 1px solid #CCCCCC" />

3.  Excel スプレッドシートのフィールドに、サブスクリプションを割り当てるユーザーの情報を入力します。 [Reference] は省略可能なフィールドです。 テンプレートに正しく入力されていない箇所があると、問題を説明するエラー メッセージが表示されます。 完了したら、ファイルをローカルに保存します。
**問題なくアップロードできるよう、次のベスト プラクティスに従ってください**。
    - フォームのどのフィールドにもコンマが含まれていないことを確認します。
    - フォームのフィールド (ユーザー名など) の前後のスペースを削除します。
    - ユーザーの名前の名または姓が 2 つの部分からなる場合、それらの間に余分なスペースがないようにします (たとえば、"Maggie May" のように 2 つの部分からなる名を "Maggie        May" と入力してはいけません。システムは余分なスペースを除去しません)。
    <img alt="Bulk add template" src="_img\assign-license-add\bulk-template.png" style="border: 1px solid #CCCCCC" />

4.  Visual Studio サブスクリプション管理ポータルに戻り、[Upload Multiple Subscribers]\(複数のサブスクライバーのアップロード\) ダイアログ ボックスで **[参照]** をクリックします。 保存した Excel ファイルを選んで、**[OK]** をクリックします。 アップロードの進行状況が画面に表示されます。 

    <img alt="Bulk add upload" src="_img\assign-license-add\bulk-assign-upload-2.png" style="border: 1px solid #CCCCCC" />

テンプレートにエラーが含まれていると、アップロードは失敗してエラーが表示されるので、テンプレートを修正して一括アップロードを再試行します。
    <img alt="Upload fail" src="_img\assign-license-add\bulk-assign-upload-fail.png" style="border: 1px solid #CCCCCC" />

アップロードが成功すると、サブスクライバーの一覧と確認メッセージが表示されます。

   <img alt="Upload complete" src="_img\assign-license-add\bulk-assign-upload-complete.png" style="border: 1px solid #CCCCCC" />