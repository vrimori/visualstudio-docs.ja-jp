---
title: "Visual Studio 2017 で問題を報告する方法 | Microsoft Docs"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.technology: vs-acquisition
ms.openlocfilehash: aec5948ed985b6ff2abde47a48198cf1a67c4337
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-report-a-problem-with-visual-studio-2017"></a>Visual Studio 2017 で問題を報告する方法
Visual Studio に問題が発生した場合は、Microsoft にお知らせください。 診断および修正を行うには、問題を以下のようにして報告してください。  

## <a name="sign-in-to-visual-studio"></a>Visual Studio にサインイン
まだサインインしていない場合は、問題を報告する前に Visual Studio にサインインします。 これで、発生している問題の報告や、問題に対するコメントへの投票ができます。 投稿されたその他の問題に投票したり、コメントしたりもできます。

1.  次のスクリーンショットに示されているように、ツールの右側にある **[サインイン]** をクリックします。
2.  画面に表示される手順に従ってサインインします。

 ![サインインして問題を報告](../ide/media/sign-in-new-ux.png "Sign in to report a problem")  

## <a name="search-and-vote-for-similar-problems"></a>類似問題を検索して投票する  
###  <a name="search_and_vote"></a>  

1.  問題を検索し、他のユーザーが既に報告しているかどうかも確認します。
2.  報告済みの場合は、"上向きの矢印に投票" してお知らせください。  

  ![類似の問題の検索と投票](../ide/media/search-and-vote.png "類似の問題の検索と投票")

## <a name="report-a-new-problem"></a>新しい問題を報告する
###  <a name="report_new_problem"></a>
1.  探している問題が見つからない場合は、画面の下部にある **[新しい問題を報告する]** ボタンをクリックします。
2.  適切な Visual Studio チームに問題を転送できるように、報告には説明的なタイトルを付けてください。
3.  可能であれば、問題を再現する手順など、さらに詳しい情報を記載します。

  ![新しい問題を報告する](../ide/media/report-new-problem.png "新しい問題を報告する")

## <a name="provide-a-screenshot-and-attachments-optional"></a>スクリーンショットと添付ファイル (省略可能) を提供する
###  <a name="provide_screenshots"></a>
 現在の画面を選んで、Microsoft に送信します。 **[追加のファイルの添付]** ボタンをクリックして、その他のスクリーン ショットやファイルをさらに添付できます。  

## <a name="provide-a-trace-and-heap-dump-optional"></a>トレースとヒープ ダンプを提供します (省略可能)  
###  <a name="provide_a_trace_and_heap_dump"></a>  

トレースとヒープ ダンプのファイルは、問題を診断するうえで役立ちます。 **[問題の報告]** ツールで再現する手順を記録し Microsoft にデータを送信してくだされば、大変助かります。  これを行う方法を次に示します。

1.  **[記録]** タブをクリックします。
2.  **[記録の開始]** をクリックします。 ツールの実行を許可します。

  ![[記録の開始] をクリックして、トレースとヒープ ダンプのファイルを提供する](../ide/media/record-dialog-box.png "トレースとヒープ ダンプ ファイルを提供する")

3.  **[ステップ記録ツール]** ツールが表示されたら、問題を再現する手順を実行します。
4.  終了したら、**[記録の停止]** ボタンをクリックします。
5.  記録された情報が Visual Studio により収集され、パッケージ化されるまでしばらく待ちます。

## <a name="submit-the-report"></a>レポートを送信します  
###  <a name="submit_the_report"></a>  
 **[送信]** ボタンをクリックして、イメージ、トレースやダンプ ファイルと共にレポートを送信します。 **[送信]** ボタンが灰色表示の場合、レポートのタイトルと説明が記載されていることを確認します。  

## <a name="see-also"></a>関連項目  
 [ご意見](../ide/talk-to-us.md)
