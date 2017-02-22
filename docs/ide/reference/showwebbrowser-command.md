---
title: "ShowWebBrowser コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "view.showwebbrowser"
helpviewer_keywords: 
  - "ShowWebBrowser コマンド"
  - "View.ShowWebBrowser コマンド"
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ShowWebBrowser コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定した URL を統合開発環境 \(IDE: Integrated Development Environment\) の内部または外部の Web ブラウザーのウィンドウに表示します。  
  
## 構文  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## 引数  
 `URL`  
 必ず指定します。  Web サイトの URL \(Uniform Resource Locator\)。  
  
## スイッチ  
 \/new  
 省略可能です。  ページを Web ブラウザーの新しいページに表示します。  
  
 \/ext  
 省略可能です。  IDE の外部にある既定の Web ブラウザーにページを表示します。  
  
## 解説  
 **ShowWebBrowser** コマンドのエイリアスは **navigate** または **nav** です。  
  
## 使用例  
 次の例は、IDE の外部にある Web ブラウザーに MSDN Online のホーム ページを表示します。  既に Web ブラウザーのページが開いている場合は、そのページを使用します。それ以外の場合は、新しいページが表示されます。  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## 参照  
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [\[検索\] ボックス](../Topic/Find-Command%20Box.md)   
 [Visual Studio コマンドの定義済みのエイリアス](../../ide/reference/visual-studio-command-aliases.md)