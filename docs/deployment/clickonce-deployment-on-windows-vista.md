---
title: Windows Vista の ClickOnce 配置 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4113c2e33e3be97a5102f5e5eca0344087a49c6
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078398"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista の ClickOnce 配置

Visual Studio でアプリケーションの構築 Windows Vista でユーザー アカウント制御 (UAC) は、通常、埋め込みマニフェストを生成するは、アプリケーションの実行可能ファイルに XML データをバイナリとしてにエンコードされます。  ClickOnce および Registration-free COM アプリケーションでは、Visual Studio は、埋め込みのマニフェストではなく、UAC のデータを格納しているこれらのプロジェクト ファイルを生成するために、外部のマニフェストが必要です。 Visual Studio の ClickOnce および Registration-free COM の展開という名前のファイルから情報を使用して*app.manifest*外部 UAC マニフェスト情報を生成します。 以外の場合は、Visual Studio には、アプリケーションの実行可能ファイルで、UAC のデータが埋め込まれます。 

Visual Studio では、マニフェスト生成のため、次のオプションを提供します。  
  
-   埋め込みマニフェストを使用します。 アプリケーションの実行可能ファイルに UAC のデータを埋め込むし、通常のユーザーとして実行します。  
  
     これは、(ClickOnce を使用する) 場合を除き、既定の設定です。 この設定は、Windows Vista で Visual Studio が動作する通常の方法をサポートしている、内部と外部の両方の世代でマニフェストを使用して`AsInvoker`します。  
  
-   外部のマニフェストを使用します。 使用して、外部のマニフェストを生成*app.manifest*します。  
  
     これで情報を使用して外部マニフェストだけが生成されます*app.manifest*します。 ClickOnce または Registration-free COM を使用してアプリケーションを発行するときに Visual Studio によって追加*app.manifest*をプロジェクトにし、このオプションを追加します。  
  
-   マニフェストを使用できません。 マニフェストを含まないアプリケーションを作成します。  
  
     このアプローチとも呼ばれます*virtualization*します。 Visual Studio の以前のバージョンからの既存のアプリケーションとの互換性のためには、このオプションを使用します。  
  
 新しいプロパティは、**アプリケーション**(Visual c# プロジェクトのみ) 用のプロジェクト デザイナーのページと、MSBuild プロジェクト ファイル形式でします。  
  
 Visual Studio IDE で UAC マニフェスト生成を構成するためのメソッドは、プロジェクトの種類 (Visual c# または Visual Basic) によって異なります。  
  
   * マニフェストの生成を Visual c# プロジェクトを構成する方法については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー (c#)](../ide/reference/application-page-project-designer-csharp.md)します。  
  
   * マニフェストの生成を Visual Basic プロジェクトを構成する方法については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ユーザーのアクセス許可と Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [[アプリケーション] ページ (プロジェクト デザイナー) (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [[アプリケーション] ページ (プロジェクト デザイナー)](../ide/reference/application-page-project-designer-visual-basic.md)