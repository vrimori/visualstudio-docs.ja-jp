---
title: "方法 : ASP.NET の例外をデバッグする | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, 例外"
  - "デバッグ [Visual Studio], ASP.NET の例外"
  - "例外, ASP.NET"
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : ASP.NET の例外をデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

例外のデバッグは、堅牢な [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションの開発で重要な部分です。  例外をデバッグする方法の一般的な情報については、「[デバッガーでの例外の管理](../debugger/managing-exceptions-with-the-debugger.md)」を参照してください。  
  
 ハンドルされない [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 例外をデバッグする場合、その例外でデバッガーを中断する必要があります。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ランタイムにはトップレベルの例外ハンドラーがあります。  そのため、デバッガーは既定では、ハンドルされない例外で実行を中断することはありません。  例外がスローされたときにデバッガーを中断するには、**\[例外\]** ダイアログ ボックスで、その例外について **\[例外が次の場合に中断する\]** で \[スローされるとき\] の設定を選択します。  
  
 "マイ コードのみ" を有効にしている場合は、**\[例外が次の場合に中断する\]** で \[スローされるとき\] を選択しても、例外が .NET Framework メソッドや他のシステム コード内でスローされても、デバッガーはすぐには中断されません。  デバッガーがシステム コード以外のコードをヒットするまで実行は継続され、ヒットした時点でデバッガーは中断されます。  つまり、例外が発生したときにシステム コードをステップ実行する必要はありません。  
  
 "マイ コードのみ" では、さらに便利な **\[例外が次の場合に中断する:\]** で \[ユーザーにハンドルされていないとき\] を選択することもできます。  例外にこの設定を選択すると、ユーザー コードで例外が取得され、処理された場合にのみ、デバッガーによってユーザー コードの実行が中断されます。  この設定では、トップレベルの [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 例外ハンドラーの効果が無視されます。この例外ハンドラーがユーザー コードではないためです。  
  
### \[マイ コードのみ\] で ASP.NET 例外を有効にするには  
  
1.  **\[デバッグ\]** メニューの **\[例外\]** をクリックします。  
  
     **\[例外\]** ダイアログ ボックスが表示されます。  
  
2.  **\[Common Language Runtime Exceptions\]** 行の **\[スローされるとき\]** または **\[ユーザーにハンドルされていないとき\]** チェック ボックスをオンにします。  
  
     **\[ユーザーにハンドルされていないとき\]** 設定を使用するには、**\[マイ コードのみ\]** を有効にする必要があります。  
  
### ASP.NET の例外処理で推奨される手順を使用するには  
  
-   予測でき、処理方法がわかる例外をスローできるコードを、`try … catch` ブロックで囲みます。  たとえば、アプリケーションから XML Web サービスを呼び出したり、SQL Server を直接呼び出したりする場合、そのコードは、**try … catch** ブロックで囲みます。この場合、数多くの例外が発生すると予想できるためです。