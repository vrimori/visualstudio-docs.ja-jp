---
title: "方法 : リボンのカスタマイズの概要"
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
  - "カスタム リボン, 追加 (リボンをプロジェクトに)"
  - "カスタマイズ (リボンを), 追加 (リボンをプロジェクトに)"
  - "リボン [Visual Studio での Office 開発], 追加"
  - "リボン [Visual Studio での Office 開発], カスタマイズ"
ms.assetid: 9eb6b8b3-1842-4cb3-8229-273ce35c64fb
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# 方法 : リボンのカスタマイズの概要
  Microsoft Office アプリケーションのリボンをカスタマイズするには、**\[リボン \(ビジュアルなデザイナー\)\]** 項目または **\[リボン \(XML\)\]** 項目を Office プロジェクトに追加します。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### リボンをプロジェクトに追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[リボン \(ビジュアル デザイナー\)\]** または **\[リボン \(XML\)\]** をクリックします。  これらのテンプレートの詳細については、「[リボンの概要](../vsto/ribbon-overview.md)」を参照してください。  
  
3.  **\[名前\]** ボックスにリボン項目の名前を入力します。  
  
     名前には、次の文字は使用できません。  
  
    -   シャープ記号 \(\#\)  
  
    -   パーセント記号 \(%\)  
  
    -   アンパサンド \(&\)  
  
    -   アスタリスク \(\*\)  
  
    -   縦棒 \(|\)  
  
    -   円記号 \(\\\)  
  
    -   コロン \(:\)  
  
    -   二重引用符 \("\)  
  
    -   不等号 \(より小\) \(\<\)  
  
    -   不等号 \(より大\) \(\>\)  
  
    -   疑問符 \(?\)  
  
    -   スラッシュ \(\/\)  
  
    -   先行する空白または後続の空白 \(' '\)  
  
    -   Windows または DOS の予約語 \("nul"、"aux"、"con"、"com1"、"lpt1" など\)  
  
4.  **\[OK\]** をクリックします。  
  
 **ソリューション エクスプローラー**にリボン項目が表示されます。  以降の手順については、「[リボンの概要](../vsto/ribbon-overview.md)」を参照してください。  
  
## 参照  
 [実行時のリボンへのアクセス](../vsto/accessing-the-ribbon-at-run-time.md)   
 [リボン デザイナー](../vsto/ribbon-designer.md)   
 [リボン XML](../vsto/ribbon-xml.md)   
 [チュートリアル : リボン デザイナーを使用したカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [チュートリアル : リボン XML によるカスタム タブの作成](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  