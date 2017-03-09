---
title: "&quot;この作業には、追加の権利が必要です&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UACDialog"
ms.assetid: a03d3509-5e6e-411a-9aec-0766d7ee3a0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &quot;この作業には、追加の権利が必要です&quot;
このエラーは、Visual Studio コマンドがアカウントに操作を完了するための適切なアクセス許可を持つユーザーが起動すると表示されます。  
  
 Visual Studio のコマンドは、必要なファイルとレジストリ キーをすべて読み取りまたは書き込みを行うコマンドを実行するために十分なユーザー アクセス権を持つアカウントで実行する必要があります。  これらの権限を取得するには、管理者のアクセスを発生させたようなアカウントで Visual Studio を終了し、開く必要があります。  
  
 アクセス許可の詳細については、Visual Studio を実行する、[ユーザーのアクセス許可](../ide/user-permissions-and-visual-studio.md)を決定する場合の。  
  
### このエラーを解決するには  
  
1.  ダイアログ ボックスの **\[別のアカウントを使用して再起動\]** をクリックします。  
  
     次に、これは現在読み込まれているソリューションの保存を確認するメッセージを表示し、Visual Studio を終了し、再起動し、別のアカウントに切り替えるように求められます。  
  
2.  ログイン プロンプトで、前のアカウントより上位の権限を持つアカウント \(Administrator など\) でログインします。  
  
     Visual Studio の起動時には、最後のソリューションとコマンド ラインを再読み込みします。  
  
> [!NOTE]
>  上位の権限を持つアカウントでログインしても、必ずしも Visual Studio コマンドが機能する保証はありません。  一部のコマンドは、管理者アカウントを使用しても正常に実行されることがあります。