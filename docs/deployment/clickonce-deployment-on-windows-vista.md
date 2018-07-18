---
title: Windows Vista の ClickOnce 配置 |Microsoft ドキュメント
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
ms.openlocfilehash: c546d7e4287fc47a3770baa306a43a1631be2f06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558933"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista の ClickOnce 配置
Visual Studio でアプリケーションの構築 Windows Vista でユーザー アカウント制御 (UAC) は、通常、埋め込みマニフェストを生成するには、アプリケーションの実行可能ファイルに XML データをバイナリとしてにエンコードされます。 ClickOnce と登録を必要としない COM アプリケーションは外部マニフェストが必要なために、Visual Studio はこれらの種類の埋め込まれたマニフェストではなく、UAC データを含むプロジェクト ファイルを生成します。 Visual Studio の既定では、ユーザーが (ClickOnce と登録を必要としない COM デプロイメント用)、外部の UAC マニフェスト情報を生成するか、アプリケーションの実行可能ファイル (それ以外の場合は) に埋め込むアプリケーション マニフェストと呼ばれるファイルから情報が使用されます。 Visual Studio には、マニフェスト生成のための次のオプションが用意されています。  
  
-   埋め込みマニフェストを使用します。 アプリケーションの実行可能ファイルに UAC のデータを埋め込むし、通常のユーザーとして実行します。  
  
     これは、(ClickOnce を使用して) しない限り、既定の設定です。 この設定は、Windows Vista; の Visual Studio が動作する通常の方法をサポートします。つまり、両方を使用して、内部および外部マニフェストの生成`AsInvoker`です。  
  
-   外部マニフェストを使用します。 アプリケーション マニフェストを使用して外部マニフェストを生成します。  
  
     これには、マニフェストに含まれる情報を使用して外部マニフェストのみが生成されます。 ClickOnce または登録を必要としない COM を使用してアプリケーションを発行するときに、Visual Studio はアプリケーション マニフェストをプロジェクトに追加し、このオプションを追加します。  
  
-   マニフェストを使用できなくなります。 マニフェストを含まないアプリケーションを作成します。  
  
     この方法とも呼ばれる*virtualization*です。 Visual Studio の以前のバージョンからの既存のアプリケーションとの互換性のためには、このオプションを使用します。  
  
 使用できる、新しいプロパティが、**アプリケーション**(Visual c# プロジェクトに対してのみ)、プロジェクト デザイナーのページと、MSBuild プロジェクト ファイル形式にします。  
  
 プロジェクトの種類 (Visual c# および Visual Basic) によって、Visual Studio IDE で UAC マニフェスト生成の構成方法が異なることに注意してください。  
  
 マニフェスト生成のための Visual c# プロジェクトの構成については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー (c#)](../ide/reference/application-page-project-designer-csharp.md)です。  
  
 マニフェスト生成のための Visual Basic プロジェクトの構成については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー) (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [ユーザーのアクセス許可と Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [[アプリケーション] ページ (プロジェクト デザイナー) (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [[アプリケーション] ページ (プロジェクト デザイナー)](../ide/reference/application-page-project-designer-visual-basic.md)