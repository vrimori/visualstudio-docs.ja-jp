---
title: '方法: Web ページ内の JavaScript コードをプロファイリングする | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f9def923e0cc012a37c02d24b67e807668ae976
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792113"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>方法: Web ページ内の JavaScript コードをプロファイリングする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイリング ツールは、インストルメンテーション プロファイリング メソッドを使用して、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web アプリケーション、任意の Web ページ、または JavaScript アプリケーションで実行する JavaScript コードのパフォーマンス データを収集できます。  
  
 **必要条件**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、 [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
-   Internet Explorer 8 以降  
  
> [!WARNING]
>  Windows ストア アプリで JavaScript をプロファイリングするには、次のトピックのいずれかをご覧ください。  
> 
> - [JavaScript 関数タイミング](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)[リモート デバイスで JavaScript 関数タイミング](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
>   -   [JavaScript 関数タイミング データを分析します。](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
>   -  
  
 プロファイル ウィザードを使用して、パフォーマンス セッションを作成できます。 インストルメンテーション メソッドを指定し、パフォーマンス セッションの [プロパティ] ダイアログ ボックスの [インストルメンテーション] ページで、JavaScript のプロファイル オプションを指定します。  
  
 JavaScript のプロファイルを指定すると、ブラウザーで実行される JavaScript コードとサーバーで実行される [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] コードのどちらもプロファイリングされます。  
  
-   [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web アプリケーションの場合、ブラウザーで実行される JavaScript コードとサーバーで実行される [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] コードのどちらもプロファイリングされます。  
  
-   任意の Web ページの場合、ブラウザーで実行される JavaScript コードがプロファイリングされます。  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>ASP.NET Web アプリケーション プロジェクトで、JavaScript をプロファイリングするには  
  
1.  [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] で、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web プロジェクトを開きます。  
  
2.  **[分析]** メニューの **[パフォーマンス ウィザードの起動]** をクリックします。  
  
3.  パフォーマンス ウィザードの最初のページで、 **インストルメンテーション** プロファイリング メソッドを指定して、 **[次へ]** をクリックします。  
  
4.  ウィザードの 2 番目のページで、ターゲットの一覧で現在のプロジェクトが選ばれていることを確認し、 **[次へ]** をクリックします。  
  
5.  ウィザードの 3 番目のページで、 **[プロファイル JavaScript]** チェック ボックスを選び、 **[次へ]** をクリックします。  
  
6.  ウィザードの 4 番目のページで、 **[完了]** をクリックして、ブラウザーで Web アプリケーションを開始します。  
  
7.  プロファイリングする機能を実行します。  
  
8.  プロファイル セッションを終了するには、ブラウザーを閉じます。  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>個々の Web ページや JavaScript アプリケーションで JavaScript をプロファイリングするには  
  
1.  [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]を開きます。  
  
2.  **[分析]** メニューの **[パフォーマンス ウィザードの起動]** をクリックします。  
  
3.  パフォーマンス ウィザードの最初のページで、 **インストルメンテーション** プロファイリング メソッドを指定して、 **[次へ]** をクリックします。  
  
4.  ウィザードの 2 番目のページで、An ASP.NET、または JavaScript のアプリケーションをクリックし、 **[次へ]** をクリックします。  
  
5.  ウィザードの 3 番目のページ:  
  
    1.  **[アプリケーションを実行する URL またはパス]** ボックスのページの URL を入力します。  
  
    2.  **[プロファイル JavaScript]** チェック ボックスを選び、 **[次へ]** をクリックします。  
  
6.  ウィザードの 4 番目のページで、 **[完了]** をクリックし、ブラウザーで Web ページを開始します。  
  
7.  プロファイリングする機能を実行します。  
  
8.  プロファイル セッションを終了するには、ブラウザーを閉じます。



