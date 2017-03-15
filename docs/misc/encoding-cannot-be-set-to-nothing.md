---
title: "エンコードは Nothing に設定できません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# エンコードは Nothing に設定できません
パラメーター `encoding` が `Nothing` に設定されていますが、正しい値が必要なため、ファイルへの読み取りまたは書き込みに失敗しました。  
  
 <xref:System.Text.Encoding> は、ファイルへの書き込み時に使用するエンコードを判別するのに使用されます。 既定は UTF\-8 です。  
  
### このエラーを解決するには  
  
-   正しい値を `encoding` パラメーターに指定します。  
  
## 参照  
 [File Encodings](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-encodings)   
 [Reading from Files](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/reading-from-files)   
 [Writing to Files](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/writing-to-files)   
 [My.Computer.FileSystem.ReadAllText メソッド](http://msdn.microsoft.com/ja-jp/3a7ac8be-fb1d-4087-bc65-167d6754d57f)   
 [My.Computer.FileSystem.WriteAllText メソッド](http://msdn.microsoft.com/ja-jp/f507460c-87d9-4504-b74f-3ff825c7d5c4)