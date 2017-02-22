---
title: "SDI サーバー アプリケーション | Microsoft Docs"
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
helpviewer_keywords: 
  - "SDI サーバー アプリケーション"
  - "SDI サーバー アプリケーション, デバッグ"
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SDI サーバー アプリケーション
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

SDI サーバー アプリケーションをデバッグする場合は、C\/C\+\+、C\#、または Visual Basic のプロジェクトの \[*Project* プロパティ ページ\] ダイアログ ボックスで、**\[コマンド ライン引数\]** プロパティに `/Embedding` または `/Automation` を指定する必要があります。  
  
 デバッガーはこれらのコマンド ライン引数を利用して、コンテナーから起動されたようにサーバー アプリケーションを起動できます。  次に、プログラム マネージャーまたはファイル マネージャーからコンテナーを起動すると、コンテナーはデバッガー中で起動されたサーバーのインスタンスを使用できます。  
  
## \[コマンド ライン引数\] プロパティの表示  
 \[*Project* プロパティ ページ\] ダイアログ ボックスを表示するには、ソリューション エクスプローラーでプロジェクトを右クリックし、ショートカット メニューの \[プロパティ\] をクリックします。  \[コマンド ライン引数\] プロパティを表示するには、\[構成プロパティ\] カテゴリを展開し、\[デバッグ\] ページをクリックします。  
  
## 参照  
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)   
 [方法 : COM サーバーをデバッグする](../Topic/How%20to:%20Debug%20COM%20Servers.md)