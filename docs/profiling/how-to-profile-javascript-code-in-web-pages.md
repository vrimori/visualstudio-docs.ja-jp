---
title: "方法: Web ページ内の JavaScript (ECMA) コードをプロファイリングする | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript のパフォーマンス プロファイル"
  - "プロファイリング ツール、JavaScript"
  - "Web サイトのパフォーマンス プロファイル"
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>方法: Web ページ内の JavaScript コードをプロファイリングする
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールは、インストルメンテーション プロファイリング メソッドを使用して、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーション、任意の Web ページ、または JavaScript アプリケーションで実行する JavaScript コードのパフォーマンス データを収集できます。  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
-   Internet Explorer 8 以降  
  
> [!WARNING]
>  Windows ストア アプリで JavaScript をプロファイリングするには、「[JavaScript メモリ](../profiling/javascript-memory.md)」をご覧ください。 
  
 プロファイル ウィザードを使用して、パフォーマンス セッションを作成できます。 インストルメンテーション メソッドを指定し、パフォーマンス セッションの [プロパティ] ダイアログ ボックスの [インストルメンテーション] ページで、JavaScript のプロファイル オプションを指定します。  
  
 JavaScript のプロファイルを指定すると、ブラウザーで実行される JavaScript コードとサーバーで実行される [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードのどちらもプロファイリングされます。  
  
-   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションの場合、ブラウザーで実行される JavaScript コードとサーバーで実行される [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードのどちらもプロファイリングされます。  
  
-   任意の Web ページの場合、ブラウザーで実行される JavaScript コードがプロファイリングされます。  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>ASP.NET Web アプリケーション プロジェクトで、JavaScript をプロファイリングするには  
  
1.  [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] で、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web プロジェクトを開きます。  
  
2.  **[分析]** メニューの **[パフォーマンス ウィザードの起動]**をクリックします。  
  
3.  パフォーマンス ウィザードの最初のページで、 **インストルメンテーション** プロファイリング メソッドを指定して、 **[次へ]**をクリックします。  
  
4.  ウィザードの&2; 番目のページで、ターゲットの一覧で現在のプロジェクトが選ばれていることを確認し、 **[次へ]**をクリックします。  
  
5.  ウィザードの&3; 番目のページで、 **[プロファイル JavaScript]** チェック ボックスを選び、 **[次へ]**をクリックします。  
  
6.  ウィザードの&4; 番目のページで、 **[完了]** をクリックして、ブラウザーで Web アプリケーションを開始します。  
  
7.  プロファイリングする機能を実行します。  
  
8.  プロファイル セッションを終了するには、ブラウザーを閉じます。  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>個々の Web ページや JavaScript アプリケーションで JavaScript をプロファイリングするには  
  
1.  [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] を開きます。  
  
2.  **[分析]** メニューの **[パフォーマンス ウィザードの起動]**をクリックします。  
  
3.  パフォーマンス ウィザードの最初のページで、 **インストルメンテーション** プロファイリング メソッドを指定して、 **[次へ]**をクリックします。  
  
4.  ウィザードの&2; 番目のページで、An ASP.NET、または JavaScript のアプリケーションをクリックし、 **[次へ]**をクリックします。  
  
5.  ウィザードの&3; 番目のページ:  
  
    1.  **[アプリケーションを実行する URL またはパス]** ボックスのページの URL を入力します。  
  
    2.  **[プロファイル JavaScript]** チェック ボックスを選び、 **[次へ]**をクリックします。  
  
6.  ウィザードの&4; 番目のページで、 **[完了]** をクリックし、ブラウザーで Web ページを開始します。  
  
7.  プロファイリングする機能を実行します。  
  
8.  プロファイル セッションを終了するには、ブラウザーを閉じます。


<!--HONumber=Feb17_HO4-->


