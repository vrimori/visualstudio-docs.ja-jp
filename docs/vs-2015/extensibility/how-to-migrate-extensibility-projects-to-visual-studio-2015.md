---
title: '方法: Visual Studio 2015 への機能拡張プロジェクトの移行 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7257bf2fa433a1d9f59f15e62b15d57944632045
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545124"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>方法: 機能拡張プロジェクトを Visual Studio 2015 に移行
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: Visual Studio 2015 への機能拡張プロジェクトの移行](https://docs.microsoft.com/visualstudio/extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015)します。  
  
次に、拡張機能をアップグレードする方法を示します。  
  
> [!IMPORTANT]
>  以前のバージョンの Visual Studio の拡張機能ソリューションのバージョンを管理する場合は、アップグレードする前に、コピーを作成することを確認します。 アップグレードされたバージョンを前の状態に戻すにくい場合があります。  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>機能拡張のソリューションをアップグレードするには  
  
1.  コピーを使用するアップグレードは、新しいバージョンで開きます。 アップグレードを元に戻すことがないことを伝えられます。  
  
2.  アップグレードの完了後は、devenv.exe の新しいバージョンに外部プログラムのパスを変更します。 プロジェクト ノードを右クリックし、**ソリューション エクスプ ローラー**を選択し、**プロパティ**します。 **デバッグ** タブで、検索によって、テキスト ボックス**外部プログラムの開始**を Visual Studio 2015 パスでは次のように devenv.exe のパスを変更して。  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Microsoft.VisualStudio.Shell.14.0.dll への参照を追加します。 (でプロジェクト ノードを右クリックし、**ソリューション エクスプ ローラー**選び、**追加/reference**します。 選択、**拡張** タブをクリックして確認**Microsoft.VisualStudio.Shell.14.0**)。  
  
4.  ソリューションをビルドします。 ビルドされたファイルがデプロイされます。  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< 作成者名\>\\< プロジェクト名\>\\< プロジェクト バージョン\>\\**します。  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>VS SDK の NuGet 参照アセンブリを拡張機能プロジェクトを更新するには  
  
1.  VS SDK 参照アセンブリがプロジェクトのニーズを決定します。  **ソリューション エクスプ ローラー**、プロジェクトの展開**参照**ノードとプロジェクトの参照の一覧を確認してください。  VS SDK の参照アセンブリは、プレフィックスが**Microsoft.VisualStudio**名 (例: Microsoft.VisualStudio.Shell.14.0)。  
  
2.  VS SDK の参照アセンブリを選択してプロジェクトから削除を右クリックし、**削除**します。  
  
3.  VS SDK の参照アセンブリの NuGet のバージョンを追加します。  **ソリューション エクスプ ローラーの参照**ノードを開いて、 **NuGet パッケージの管理.** ダイアログ ボックス。  このダイアログ ボックスの詳細については、表示[ダイアログによる NuGet パッケージの管理](http://docs.nuget.org/Consume/Package-Manager-Dialog)します。 VS SDK の参照アセンブリが で公開されている[nuget.org](http://www.nuget.org)によって[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)します。  
  
4.  使用して**nuget.org**として、**パッケージ ソース**、必要な参照アセンブリに一致する NuGet パッケージ名の検索 (例: Microsoft.VisualStudio.Shell.14.0) でインストールし、プロジェクトです。  NuGet は、初期のアセンブリの依存関係を満たすために複数の参照アセンブリを追加する可能性があります。  
  
     VS SDK をインストールして VS SDK のすべての参照アセンブリが一度に追加できる場合は、[メタ パッケージ](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)します。  
  
5.  NuGet のバージョンの VS SDK ビルド ツールの使用に切り替えることもできます。 この NuGet パッケージは[Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools)に 1 回追加し、プロジェクトが必要なツールを含むし、VS SDK をインストールせず、コンピューターで、機能拡張プロジェクトをビルドできるようにファイルを対象します。  
  
> [!NOTE]
>  ない NuGet 参照アセンブリおよびツールを使用する既存の機能拡張プロジェクトを更新することが必要です。  参照アセンブリと VS SDK と共にインストールされるツールを使用してビルドを継続できます。

