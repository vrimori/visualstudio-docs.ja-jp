---
Title: "Visual Studio サブスクリプションにライセンスを割り当てる"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: "管理者がサブスクライバーにライセンスを割り当てる方法を説明します"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: e2a32e911c85603b2d08adb0edad76bcfbc6d6ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Visual Studio サブスクリプション管理者ポータルでライセンスを割り当てる
## <a name="assigning-a-single-user"></a>1 人のユーザーの割り当て
Visual Studio サブスクリプションに利用可能なライセンスがある場合は、新しいユーザーにそのライセンスを割り当てて、サブスクリプションの特典にアクセスできるようにすることができます。 
1.  1 人の Visual Studio サブスクライバーを割り当てるには、テーブルの上部にある **[追加]** をクリックします。

![サブスクライバーの追加](_img\assign-license-add\assign-license-add.png)

2.  フォームのフィールドに新しいサブスクライバーの情報を入力します。 組織が Azure Active Directory を使っている場合は、このフィールドを使って現在のディレクトリのユーザーを検索し、検索結果から適切なユーザーを選ぶことができます。 ユーザーを選ぶと、名前、サインイン メール アドレス、通知メール アドレスが自動的に設定されます (下図参照)。 

サインイン用とメール受信用に異なるメール アドレスが使われている場合は、ここでそれを入力できます。 [Different email for communication than sign-in?]\(通信用とサインイン用の電子メール アドレスが異なる\) ハイパーリンクを選びます。 

このサブスクライバーに、[Visual Studio サブスクリプション ポータル](https:/my.visualstudio.com)へのサインインおよびソフトウェア ダウンロードと他のすべてのサブスクリプション サービスおよびリソース (Microsoft Azure、Visual Studio Team Services、Xamarin と Pluralsight のトレーニング、テクニカル サポート、その他) へのアクセスを許可する場合は、"ダウンロード" ボックスをオンのままにします。 このボックスをオフにすると、ユーザーはソフトウェアのダウンロードにアクセスできなくなりますが、サブスクリプションに含まれる他のすべての特典へのアクセスには影響ありません。 終わったら、**[追加]** をクリックします。

![サブスクライバー情報の入力](_img\assign-license-add\add-subscriber-1.png)
![サブスクライバー情報の入力](_img\assign-license-add\add-subscriber-2.png)

3.  サブスクライバーを追加すると、詳細な説明が記載された割り当てメールがサブスクライバーに自動的に送信されます。 上部メニューの [再送信] ボタンをクリックすることで、いつでも割り当てメールを送信し直すことができます。

![追加されたサブスクライバー](_img\assign-license-add\add-subscriber-complete.png)

## <a name="bulk-assignments"></a>一括割り当て
1.  複数のサブスクライバーを一度に追加するには、[サブスクライバー] タブに移動します。上部リボンの **[一括追加]** をクリックします。 

![一括追加](_img\assign-license-add\bulk-assign-add.png)

2. 一括割り当てでは、Microsoft Excel テンプレートを使ってサブスクライバーをアップロードします。 [Upload Multiple Subscribers]\(複数のサブスクライバーのアップロード\) ダイアログ ボックスで、**[ダウンロード]** をクリックしてテンプレートをダウンロードします。 常にこのテンプレートの最新バージョンをダウンロードしてください。 古いバージョンを使うと、一括アップロードが失敗する可能性があります。
!複数のサブスクライバーのアップロード](_img\assign-license-add\bulk-assign-upload.png)
3.  Excel スプレッドシートのフィールドに、サブスクリプションを割り当てるユーザーの情報を入力します。 [Reference] は省略可能なフィールドです。 テンプレートに正しく入力されていない箇所があると、問題を説明するエラー メッセージが表示されます。 終了したら、ハード ドライブにファイルを保存します。
**問題なくアップロードできるよう、次のベスト プラクティスに従ってください**。
- フォームのどのフィールドにもコンマが含まれていないことを確認します。
- フォームのフィールド (ユーザー名など) の前後のスペースを削除します。
- ユーザーの名前の名または姓が 2 つの部分からなる場合、それらの間に余分なスペースがないようにします (たとえば、"Maggie May" のように 2 つの部分からなる名を "Maggie        May" と入力してはいけません。システムは余分なスペースを除去しません)。

![一括追加テンプレート](_img\assign-license-add\bulk-template.png)

4.  Visual Studio サブスクリプション管理ポータルに戻り、[Upload Multiple Subscribers]\(複数のサブスクライバーのアップロード\) ダイアログ ボックスで **[参照]** をクリックします。 保存した Excel ファイルを選んで、**[OK]** をクリックします。 アップロードの進行状況が画面に表示されます。 

![一括追加のアップロード](_img\assign-license-add\bulk-assign-upload-2.png)

テンプレートにエラーが含まれていると、アップロードは失敗してエラーが表示されるので、テンプレートを修正して一括アップロードを再試行します。

![アップロード失敗](_img\assign-license-add\bulk-assign-upload-fail.png)

アップロードが成功すると、サブスクライバーの一覧と確認メッセージが表示されます。

![アップロード完了](_img\assign-license-add\bulk-assign-upload-complete.png)