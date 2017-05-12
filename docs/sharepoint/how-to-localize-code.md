---
title: "方法: コードをローカライズする"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ローカライズ (コードを) [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, ローカライズ"
ms.assetid: 0e852052-5ad4-4517-81cf-8865ec304441
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 方法: コードをローカライズする
  ローカライズされていないコードでは、ハードコーディングされた文字列値が使用されています。  コードの文字列をローカライズするには、それらを <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> の呼び出しに置き換えます。このメソッドは、ローカライズされたリソースを参照します。  
  
## コードのローカライズ  
  
#### コードをローカライズするには  
  
1.  **ソリューション エクスプローラー**で、プロジェクト項目のショートカット メニューを開き、**\[追加\]**、**\[モジュール\]** の順に選択します。  
  
     **\[リソース ファイル\]** テンプレートを選択します。  
  
    > [!NOTE]  
    >  Deployment Type プロパティを使用できるように、SharePoint プロジェクト項目にリソース ファイルを必ず追加します。  このプロパティは、後で必要になります。  
  
2.  既定の言語のリソース ファイルには、.resx 拡張子が付いた任意の名前を付けます \(MyAppResources.resx など\)。  
  
3.  ローカライズ言語ごとに手順 1. と 2. を繰り返して、SharePoint プロジェクト項目にそれぞれのリソース ファイルを追加します。  
  
     ローカライズされた各リソース ファイルに対しては、同じ基本名にカルチャ ID を加えた名前を使用します   \(ドイツ語の場合は MyAppResources.de\-DE.resx など\)。  
  
4.  各リソース ファイルを開いて、ローカライズされた文字列を追加します。  各ファイルで同じ文字列 ID を使用します。  
  
5.  各リソース ファイルの **\[配置タイプ\]** プロパティの値を **\[AppGlobalResource\]** に変更して、サーバーの App\_GlobalResources フォルダーに配置されるようにします。  
  
6.  各ファイルの **\[ビルド アクション\]** プロパティの値は **\[埋め込まれたリソース\]** のままにします。  
  
     埋め込みリソースはプロジェクトの DLL にコンパイルされます。  
  
7.  プロジェクトをビルドして、リソースのサテライト DLL を作成します。  
  
8.  **パッケージ デザイナー**で、**\[詳細設定\]** タブをクリックし、サテライト アセンブリを追加します。  
  
9. **\[場所\]** ボックスで、場所のパスの先頭にカルチャ ID のフォルダーを追加します \(de\-DE\\*Project Item Name*.resources.dll など\)。  
  
10. ソリューションで System.Web アセンブリがまだ参照されていない場合は System.Web アセンブリへの参照を追加し、<xref:System.Web> に対するディレクティブをコードに追加します。  
  
11. UI テキスト、エラー、メッセージ テキストなど、ユーザーへの表示用にコード内でハードコーディングされている文字列をすべて見つけます。  それらの文字列を、次の構文を使用する <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> メソッドの呼び出しに置き換えます。  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. F5 キーを押してアプリケーションをビルドし、実行します。  
  
13. SharePoint で、表示言語を既定の言語から変更します。  
  
     ローカライズされた文字列がアプリケーションに表示されます。  ローカライズされたリソースを表示するには、リソース ファイルのカルチャに対応する Language Pack が SharePoint サーバーにインストールされている必要があります。  
  
## 参照  
 [SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)   
 [方法: フィーチャーをローカライズする](../sharepoint/how-to-localize-a-feature.md)   
 [方法: ASPX マークアップをローカライズする](../sharepoint/how-to-localize-aspx-markup.md)   
 [方法: リソース ファイルを追加する](../sharepoint/how-to-add-a-resource-file.md)  
  
  