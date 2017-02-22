---
title: "チュートリアル : デザイン時のデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ブレークポイント, デザイン時デバッグ"
  - "デバッグ [Visual Studio], デザイン時"
  - "デザイン時デバッグ"
  - "イミディエイト ウィンドウ, デザイン時デバッグ"
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# チュートリアル : デザイン時のデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio の **\[イミディエイト\]** ウィンドウを使用すると、アプリケーションを実行しなくても、関数やサブルーチンを実行できます。  関数またはサブルーチンにブレークポイントが含まれているとき、適切なポイントで実行を中断します。  デバッガー ウィンドウを使用して、プログラムの状態を確認できます。  この機能は、デザイン時のデバッグと呼ばれます。  
  
 次に、この機能の操作手順を説明します。  
  
### \[イミディエイト\] ウィンドウからブレークポイントにヒットするには  
  
1.  次のコードを Visual Basic コンソール アプリケーションに貼り付けます。  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  `s="Add BreakPoint Here"` という行にブレークポイントを設定します。  
  
3.  **\[イミディエイト\]** ウィンドウに「`?MyFunction<enter>`」と入力します。  
  
4.  ブレークポイントにヒットしたことと、呼び出し履歴が正確であることを確認します。  
  
5.  **\[デバッグ\]** の **\[続行\]** をクリックし、まだデザイン モードであることを確認します。  
  
6.  **\[イミディエイト\]** ウィンドウに「`?MyFunction<enter>`」と入力します。  
  
7.  **\[イミディエイト\]** ウィンドウに「`?MySub<enter>`」と入力します。  
  
8.  ブレークポイントにヒットすることを確認し、**\[ローカル\]** ウィンドウで静的変数 `i` の値を調べます。  3 という値が表示されます。  
  
9. 呼び出し履歴が正確であることを確認します。  
  
10. **\[デバッグ\]** の **\[続行\]** をクリックし、まだデザイン モードであることを確認します。  
  
## 参照  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)