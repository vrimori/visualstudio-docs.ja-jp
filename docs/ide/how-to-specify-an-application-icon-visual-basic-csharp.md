---
title: "方法 : アプリケーション アイコンを指定する (Visual Basic、C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: ce92aef6f676cbdd35142f058312af90581900c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>方法 : アプリケーション アイコンを指定する (Visual Basic、C#)
プロジェクトの `Icon` プロパティは、ファイル エクスプローラーと Windows タスク バーに表示されるコンパイルされたアプリケーションのアイコン ファイル (.ico) を指定します。  
  
 `Icon` プロパティには、**プロジェクト デザイナー**の **[アプリケーション]** ウィンドウからアクセスできます。このプロパティには、リソースまたはコンテンツ ファイルとしてプロジェクトに追加されているアイコンの一覧が含まれています。  
  
> [!NOTE]
>  アプリケーションのアイコン プロパティを設定した後、アプリケーション内の各 **Window** または **Form** の `Icon` プロパティを設定することもできます。 Windows Presentation Foundation (WPF) スタンドアロン アプリケーションのウィンドウ アイコンの詳細については、<xref:System.Windows.Window.Icon%2A> プロパティを参照してください。  
  
### <a name="to-specify-an-application-icon"></a>アプリケーション アイコンを指定するには  
  
1.  **ソリューション エクスプローラー**で、**[ソリューション]** ノードではなくプロジェクト ノードを選びます。  
  
2.  メニュー バーで、**[プロジェクト]**、**[プロパティ]** の順に選びます。  
  
3.  **プロジェクト デザイナー**が表示されたら、**[アプリケーション]** タブを選びます。  
  
4.  **(Visual Basic)** **[アイコン]** 一覧で、アイコン (.ico) ファイルを選びます。  
  
     **(C#)** **[アイコン]** 一覧の近くにある **[参照]** ボタンを選び、使うアイコン ファイルの場所を参照します。  
  
## <a name="see-also"></a>参照  
 [[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [[アプリケーション] ページ (プロジェクト デザイナー) (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [アプリケーション プロパティの管理](../ide/application-properties.md)  
 [方法: リソースを追加または削除する](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)