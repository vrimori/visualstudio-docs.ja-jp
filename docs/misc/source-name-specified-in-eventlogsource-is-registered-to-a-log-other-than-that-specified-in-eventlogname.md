---
title: "EventLogSource で指定したソース名は、EventLogName で指定したログ以外のログに登録されています | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# EventLogSource で指定したソース名は、EventLogName で指定したログ以外のログに登録されています
`EventLog` が、別のログに登録されているソースを参照しようとしています。 イベント ログにエントリを書き込んでいる場合は、<xref:System.Diagnostics.EventLog.Source%2A> プロパティを指定する必要があります。<xref:System.Diagnostics.EventLog.Source%2A> プロパティはコンポーネントを有効なエントリのソースとしてイベント ログに登録します。 1 つのソースは一度に 1 つのイベント ログにのみ関連付ける \(つまり、エントリを書き込む\) ことができます。  
  
 既定では、先にコンポーネントを有効なソースとして登録しないでエントリを書き込もうとした場合、<xref:System.Diagnostics.EventLog.Source%2A> プロパティの値をソース文字列として使用して、自動的にソースがイベント ログに登録されます。  
  
### このエラーを解決するには  
  
-   ソースが、正しいログに登録されていることを確認します。 これを行うには、<xref:System.Diagnostics.EventLog.CreateEventSource%2A> メソッドまたをそのオーバーロードのいずれかを使用して、コンポーネントを一意に識別する文字列をイベント ログに指定します。  
  
## 参照  
 [Administering Event Logs](http://msdn.microsoft.com/ja-jp/35f53238-bdd2-417b-acd8-2fd9f7397f18)   
 [Event Log References](http://msdn.microsoft.com/ja-jp/4af0661c-6c96-49f4-961d-b26ed9bc3e87)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/ja-jp/948ff920-a739-4e66-a191-ee951512d42c)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/ja-jp/bc66c900-4b8a-426a-b8e2-17031a20167e)