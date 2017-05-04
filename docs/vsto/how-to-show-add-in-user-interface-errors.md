---
title: "方法 : アドインのユーザー インターフェイス エラーを表示する | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "アドイン [Visual Studio での Office 開発]、ユーザー インターフェイス エラー"
  - "エラー [Visual Studio での Office 開発]、ユーザー インターフェイス エラー"
  - "ユーザー インターフェイス [Visual Studio での Office 開発]、エラー"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]、ユーザー インターフェイス エラー"
ms.assetid: aa82cc04-e616-4501-940c-79d11fb393cc
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 方法 : アドインのユーザー インターフェイス エラーを表示する
  既定では、VSTO アドインが Microsoft Office ユーザー インターフェイス \(UI\) の操作を試みて失敗しても、エラー メッセージは表示されません。 しかし、UI に関連するエラー メッセージを表示するように Microsoft Office アプリケーションを構成できます。 これらのメッセージを使用すると、カスタム リボンが表示されない原因や、リボンは表示されるもののコントロールが表示されない理由を判断するのに役立ちます。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### VSTO アドインのユーザー インターフェイス エラーを表示するには  
  
1.  アプリケーションを起動します。  
  
2.  **\[ファイル\]** タブをクリックします。  
  
3.  **\[オプション\]** をクリックします。  
  
4.  \[カテゴリ\] ウィンドウで **\[詳細\]** をクリックします。  
  
5.  詳細ウィンドウで、**\[VSTO アドイン ユーザー インターフェイスのエラーを表示する\]** を選び、**\[OK\]** をクリックします。  
  
    > [!NOTE]  
    >  Outlook の場合、詳細ウィンドウの **\[開発\]** セクションに **\[VSTO アドイン ユーザー インターフェイスのエラーを表示する\]** チェック ボックスがあります。 その他のアプリケーションの場合、このチェック ボックスは、詳細ウィンドウの **\[全般\]** セクションにあります。  
  
## 参照  
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)   
 [Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)   
 [リボンの概要](../vsto/ribbon-overview.md)   
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)  
  
  