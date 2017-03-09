---
title: "ログのストリームを取得できません | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrApplicationLog_ExhaustedPossibleStreamNames"
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ログのストリームを取得できません
ログのストリームを取得できません。 \<name\> に基づく、可能性のあるファイル名は既に使用されています。  
  
 \<name\> に基づく、可能性のあるすべてのログ ファイル名が既に使用されているため、<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> クラスは新しいログ ファイルを作成できませんでした。  
  
 ログ ファイルが多すぎる場合、アプリケーションにアーキテクチャの問題がある可能性があります。 詳細については、<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> クラスのドキュメントを参照してください。  
  
### このエラーを解決するには  
  
1.  <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> プロパティを <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> または <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption> に設定して、ログ ファイル名に日付スタンプを含めます。  
  
2.  既存のログをアーカイブし、それらをコンピューターから削除して、<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> オブジェクトが新しいログを作成できるようにします。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>   
 [My.Application.Log オブジェクト](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [My.Log Object](/dotnet/visual-basic/language-reference/objects/my-log-object)