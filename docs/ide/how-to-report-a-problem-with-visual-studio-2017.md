---
title: "Visual Studio 2017 で問題を報告する方法 | Microsoft Docs"
ms.custom: 
ms.date: 2016-10-05
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
caps.latest.revision: 4
author: TerryGLee
ms.author: tglee
manager: ghogen
robots: noindex,nofollow
translationtype: Human Translation
ms.sourcegitcommit: b81a082de053b11e8dbe05317f69d4bcb603f4de
ms.openlocfilehash: 5aac18786f3952648eeea4e7d0258a5e59c497c2

---
# <a name="how-to-report-a-problem-with-visual-studio-2017-rc"></a>Visual Studio 2017 RC で問題を報告する方法
Visual Studio で問題が発生した場合、Microsoft に報告していただければ、診断して修正いたします。  **[問題の報告]** ツールを使うと、問題に関する詳しい情報を収集し、ボタンを数回のクリックするだけで問題を Microsoft に送信できます。  

 Microsoft は、お客様のプライバシーを尊重いたします。 お客様から送信していただいたデータの扱いについて詳しくは、「[Microsoft Visual Studio 製品ファミリのプライバシーに関する声明](https://www.visualstudio.com/en-us/dn948229)」をご覧ください。  

## <a name="open-the-report-a-problem-tool"></a>[問題の報告] ツールを開きます  
 タイトル バーで **[クイック起動]** の横にあるユーザー フィードバック アイコンをクリックするか、**[ヘルプ &#124; フィードバックの送信 &#124; 問題の報告]** の順にクリックします。  

 ![[問題の報告] メニュー項目](../ide/media/report-a-problem-menu-item.png "[問題の報告] メニュー項目")  

## <a name="search-and-vote-for-similar-problems"></a>類似問題を検索して投票する  
###  <a name="search_and_vote"></a>  

1.  問題を検索し、他のユーザーが既に報告しているかどうかを確認します。
2.  報告済みの場合は、"上向きの矢印に投票" してお知らせください。  

  ![VS15-FeedbackTool-SearchForSimilarReportedProblems](../ide/media/feedbacktool-searchforsimilarreportedproblems.png "類似問題を検索して投票する")


## <a name="report-a-new-problem"></a>新しい問題を報告する
###  <a name="report_new_problem"></a>
1.  Visual Studio の **[問題の報告]** ツールの左下にある **[+]** ボタンをクリックします。  
2.  適切な Visual Studio チームに問題を転送できるように、報告には説明的なタイトルを付けてください。  
3.  可能であれば、問題を再現する手順など、さらに詳しい情報を記載します。  

  ![VS15-FeedbackTool-ReportANewProblem](../ide/media/feedbacktool-reportanewproblem.jpg "新しい問題を報告する")

## <a name="provide-a-screenshot-and-attachments-optional"></a>スクリーンショットと添付ファイル (省略可能) を提供する
###  <a name="provide_screenshots"></a>
 現在の画面を選んで、Microsoft に送信します。 **[追加のファイルの添付]** ボタンをクリックして、その他のスクリーン ショットやファイルをさらに添付できます。  

## <a name="provide-a-trace-and-heap-dump-optional"></a>トレースとヒープ ダンプを提供します (省略可能)  
###  <a name="provide_a_trace_and_heap_dump"></a>  

トレースとヒープ ダンプのファイルは、問題を診断するうえで非常に役立ちます。   **[問題の報告]** ツールで再現する手順を記録し Microsoft にデータを送信してくだされば、大変助かります。  これを行う方法を次に示します。

1.  **[記録]** タブをクリックします。
2.  **[記録の開始]** をクリックします。 ツールの実行を許可します。
3.  **[ステップ記録ツール]** ツールが表示されたら、問題を再現する手順を実行します。
4.  終了したら、フローティング ウィンドウで **[記録の停止]** ボタンをクリックします。
5.  記録された情報が Visual Studio により収集され、パッケージ化されるまでしばらく待ちます。  終了すると、次のようなダイアログが表示されます。   

  ![VS15-FeedbackTool-AddAttachments-TraceAndHeapDumpFiles](../ide/media/feedbacktool-addattachments-traceandheapdumpfiles.jpg "トレースとヒープ ダンプ ファイルを提供する")


## <a name="submit-the-report"></a>レポートを送信します  
###  <a name="submit_the_report"></a>  
 **[送信]** ボタンをクリックして、イメージ、トレースやダンプ ファイルと共にレポートを送信します。 **[送信]** ボタンが灰色表示の場合、レポートのタイトルと説明が記載されていることを確認します。  

## <a name="see-also"></a>関連項目  
 [ご意見](../ide/talk-to-us.md)



<!--HONumber=Feb17_HO4-->


