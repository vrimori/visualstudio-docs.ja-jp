---
title: Windows Vista の ClickOnce 配置 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: a0b8b4b5cff478a2dbe03f3f72115da3c0696c4e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852062"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista の ClickOnce 配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio でアプリケーションの構築 Windows Vista でユーザー アカウント制御 (UAC) は、通常、埋め込みマニフェストを生成するは、アプリケーションの実行可能ファイルに XML データをバイナリとしてにエンコードされます。 ClickOnce および Registration-free COM アプリケーションでは、外部のマニフェストが必要とするため、Visual Studio には、これらの種類の埋め込みのマニフェストではなく、UAC のデータを含むプロジェクト ファイルが生成されます。 既定では、Visual Studio は (ClickOnce および Registration-free COM、展開用) の外部 UAC マニフェスト情報を生成するか (他のすべてのケース) のアプリケーションの実行可能ファイルに埋め込むことをアプリケーション マニフェストをという名前のファイルから情報を使用します。 Visual Studio では、マニフェスト生成のため、次のオプションを提供します。  
  
- 埋め込みマニフェストを使用します。 アプリケーションの実行可能ファイルに UAC のデータを埋め込むし、通常のユーザーとして実行します。  
  
   これは、(ClickOnce を使用する) 場合を除き、既定の設定です。 この設定は、Windows Vista の Visual Studio が動作する通常の方法をサポートします。つまり、両方を使用して内部および外部のマニフェストの生成`AsInvoker`します。  
  
- 外部のマニフェストを使用します。 アプリケーション マニフェストを使用して、外部のマニフェストを生成します。  
  
   これには、マニフェストに含まれる情報を使用して外部マニフェストだけが生成されます。 ClickOnce または Registration-free COM を使用してアプリケーションを発行するときに、Visual Studio はアプリケーション マニフェストをプロジェクトに追加し、このオプションを追加します。  
  
- マニフェストを使用できません。 マニフェストを含まないアプリケーションを作成します。  
  
   このアプローチとも呼ばれます*virtualization*します。 Visual Studio の以前のバージョンからの既存のアプリケーションとの互換性のためには、このオプションを使用します。  
  
  新しいプロパティは、**アプリケーション**(Visual c# プロジェクトのみ) 用のプロジェクト デザイナーのページと、MSBuild プロジェクト ファイル形式でします。  
  
  プロジェクトの種類 (Visual c# および Visual Basic) に応じて、Visual Studio IDE で UAC マニフェスト生成の構成方法が異なることに注意してください。  
  
  マニフェストの生成を Visual c# プロジェクトを構成する方法については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー (c#)](../ide/reference/application-page-project-designer-csharp.md)します。  
  
  マニフェストの生成を Visual Basic プロジェクトを構成する方法については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ユーザーのアクセス許可と Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [[アプリケーション] ページ (プロジェクト デザイナー) (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [[アプリケーション] ページ (プロジェクト デザイナー)](../ide/reference/application-page-project-designer-visual-basic.md)



