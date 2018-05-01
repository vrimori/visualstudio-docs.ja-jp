---
title: Visual Studio 2017 で問題を報告する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/11/2018
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: TerryGLee
ms.author: tglee
manager: douge
ms.technology: vs-acquisition
ms.workload:
- multiple
ms.openlocfilehash: eacb6ba97f79f2c66444bc79b11c51ef01a50672
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-report-a-problem-with-visual-studio-2017"></a>Visual Studio 2017 で問題を報告する方法

Visual Studio に問題が発生した場合は、Microsoft にお知らせください。 診断および修正を行うには、問題を以下のようにして報告してください。

## <a name="sign-in-to-visual-studio"></a>Visual Studio にサインイン

まだサインインしていない場合は、問題を報告する前に Visual Studio にサインインします。 これで、発生している問題の報告や、問題に対するコメントへの投票ができます。 投稿されたその他の問題に投票したり、コメントしたりもできます。

1. Visual Studio で、**[ヘルプ]** > **[フィードバックの送信]** > **[問題の報告]** の順に選びます。
2. サインインしていない場合は、次のスクリーンショットに示されているように、ツールの右側にある **[サインイン]** を選びます。
3. 画面に表示される手順に従ってサインインします。

 ![サインインして問題を報告](../ide/media/sign-in-new-ux.png "Sign in to report a problem")  

## 類似問題を検索して投票する<a name="search_and_vote"></a>

1. 問題を検索し、他のユーザーが既に報告しているかどうかも確認します。
2. 報告済みの場合は、"上向きの矢印に投票" してお知らせください。

  ![類似の問題の検索と投票](../ide/media/search-and-vote.png "類似の問題の検索と投票")

## 新しい問題を報告する<a name="report_new_problem"></a>

1. 探している問題が見つからない場合は、画面の下部にある **[新しい問題を報告する]** ボタンを選択します。
2. 適切な Visual Studio チームに問題を転送できるように、報告には説明的なタイトルを付けてください。
3. 可能であれば、問題を再現する手順など、さらに詳しい情報を記載します。

  ![新しい問題を報告する](../ide/media/report-new-problem.png "新しい問題を報告する")

## スクリーンショットと添付ファイル (省略可能) を提供する<a name="provide_screenshots"></a>

 現在の画面を選んで、Microsoft に送信します。 **[追加のファイルの添付]** ボタンを選択して、その他のスクリーン ショットやファイルをさらに添付できます。

## トレースとヒープ ダンプを提供する (省略可能)<a name="provide_a_trace_and_heap_dump"></a>

トレースとヒープ ダンプのファイルは、問題を診断するうえで役立ちます。 **[問題の報告]** ツールで再現する手順を記録し Microsoft にデータを送信してくだされば、大変助かります。 これを行う方法を次に示します。

1. **[記録]** タブを選択します。
2. **[記録の開始]** を選択します。 ツールの実行を許可します。

  ![[記録の開始] を選択して、トレースとヒープ ダンプのファイルを提供する](../ide/media/record-dialog-box.png "トレースとヒープ ダンプ ファイルを提供する")

3. **[ステップ記録ツール]** ツールが表示されたら、問題を再現する手順を実行します。
4. 終了したら、**[記録の停止]** ボタンをクリックします。
5. 記録された情報が Visual Studio により収集され、パッケージ化されるまでしばらく待ちます。

## レポートを送信する<a name="submit_the_report"></a>

 **[送信]** ボタンを選択して、イメージ、トレースやダンプ ファイルと共にレポートを送信します  (**[送信]** ボタンが灰色表示の場合、レポートのタイトルと説明が記載されていることを確認します)。

## 代替レポート <a name="alternate_reporting"></a>

### <a name="report-a-problem-by-using-the-visual-studio-installer"></a>Visual Studio インストーラーを使用して問題をレポートする

Visual Studio のインストールを完了できない場合、または Visual Studio 内のフィードバック ツールにアクセスできない場合は、**Visual Studio インストーラー**を使用して問題をレポートすることもできます。 そのためには、**Visual Studio インストーラー**の右上隅にあるフィードバック アイコンを選択します。

 ![Visual Studio インストーラーの [フィードバックの送信] ボタンからフィードバック ツールを開くことができます](../install/media/report-a-problem.png)

### <a name="search-for-problems-and-solutions-by-using-the-visual-studio-developer-community"></a>Visual Studio 開発者コミュニティを使用して問題と解決策を検索する

Visual Studio を使って問題を報告することが望ましくない場合、またはできない場合は、Visual Studio の開発者コミュニティで既に問題が報告され、解決策が投稿されている可能性があります。 詳細については、[Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/) ページを参照してください。

#### <a name="provide-product-feedback-or-a-suggestion"></a>製品に関するフィードバックや提案を提供する

レポートする問題はないが、製品に関するフィードバックや提案を提供したい場合、そのための場所も用意されています。 詳細については、[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-ide) ページを参照してください。

## <a name="see-also"></a>関連項目

* [ご意見](../ide/talk-to-us.md)
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)
