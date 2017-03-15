---
title: "Web コントロール ライブラリ (マネージ コード) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "デバッグ [Visual Studio], Web コントロール ライブラリ"
  - "デバッグ (DLL を)"
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# Web コントロール ライブラリ (マネージ コード)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Web コントロール ライブラリ プロジェクト テンプレートは DLL を作成します。  クラス ライブラリは DLL であるため、直接実行することはできません。  コントロールを埋め込む [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ページを作成する必要があります。  詳細については、「[Web Control Library Template](http://msdn.microsoft.com/ja-jp/00666b07-71d2-4ace-a13c-cc130a3ce372)」を参照してください。  
  
### Web コントロール ライブラリをデバッグするには \(方法 1\)  
  
1.  既存の Web コントロール ライブラリ プロジェクトを開くか、新しいプロジェクトを作成します。  
  
2.  コントロールを埋め込む [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ページを作成します。  
  
3.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] テスト ハーネスをホストしている Web サイトで、`/Code` という名前のサブディレクトリを作成します。  
  
4.  コントロールのソース コードを `/Code` サブディレクトリにコピーします。  
  
5.  `/Code` サブディレクトリでソース コードを開き、ブレークポイントを設定します。  
  
6.  テスト ハーネスを指す URL を使用してブラウザー ウィンドウを開きます。  コントロール内のブレークポイントにヒットすると、デバッグを開始できます。  
  
### Web コントロール ライブラリをデバッグするには \(方法 2\)  
  
1.  ホスト アプリケーション プロジェクトと Web コントロール プロジェクトを同じソリューションで作成します。  
  
2.  **ソリューション エクスプローラー**で、ホスト アプリケーションを右クリックし、**\[参照の追加\]** をクリックします。  
  
3.  Web コントロール プロジェクトへの参照を追加します。  
  
## 参照  
 [ASP.NET Web アプリケーション](../debugger/debugging-preparation-aspnet-web-applications.md)