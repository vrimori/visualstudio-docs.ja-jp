---
title: "方法: Visual Studio 2015 への機能拡張プロジェクトの移行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 016e609acb7ad837580b4cabb6055169ac7357c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>方法: Visual Studio 2015 への機能拡張プロジェクトの移行
次に、拡張機能をアップグレードする方法を示します。  
  
> [!IMPORTANT]
>  以前のバージョンの Visual Studio の拡張機能ソリューションのバージョンを管理する場合は、アップグレードする前に、コピーを作成することを確認します。 アップグレードされたバージョンを前の状態に戻すことが困難がある可能性があります。  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>拡張機能ソリューションをアップグレードするには  
  
1.  コピーを使用するアップグレードは、新しいバージョンで開きます。 メッセージが表示されます、アップグレードを元に戻すことがないことです。  
  
2.  アップグレードの完了後に、新しいバージョンの devenv.exe への外部プログラムのパスを変更します。 プロジェクト ノードを右クリックし、**ソリューション エクスプ ローラー**、順に選択**プロパティ**です。 **デバッグ** タブで、検索して、テキスト ボックス**外部プログラムの開始**し、次のようになりますが、Visual Studio 2015 パスに devenv.exe のパスを変更します。  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Microsoft.VisualStudio.Shell.14.0.dll への参照を追加します。 (でプロジェクト ノードを右クリックし、**ソリューション エクスプ ローラー**を選択し**追加/reference**です。 Select、**拡張** タブを確認し、 **Microsoft.VisualStudio.Shell.14.0**)。  
  
4.  ソリューションをビルドします。 ビルドされたファイルが展開されています。  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< 作成者名\>\\< プロジェクト名\>\\< プロジェクト バージョン\>\\** .  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>VS SDK の NuGet の参照をアセンブリに、拡張機能プロジェクトを更新するには  
  
1.  プロジェクトが必要な VS SDK の参照アセンブリを決定します。  **ソリューション エクスプ ローラー**、プロジェクトの展開**参照**ノードとプロジェクト参照の一覧を確認します。  VS SDK の参照アセンブリは、プレフィックスが**Microsoft.VisualStudio**名 (例: Microsoft.VisualStudio.Shell.14.0)。  
  
2.  VS SDK の参照アセンブリをプロジェクトから選択して削除を右クリックし、**削除**です。  
  
3.  NuGet のバージョンの VS SDK の参照アセンブリを追加します。  **ソリューション エクスプ ローラーの参照**ノードを開いて、 **NuGet パッケージを管理しています.**ダイアログ。  このダイアログ ボックスの詳細につく場合は、「[パッケージ マネージャー UI](http://docs.microsoft.com/NuGet/Tools/Package-Manager-UI)です。 VS SDK の参照アセンブリの発行は  [nuget.org](http://www.nuget.org)によって[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)です。  
  
4.  使用して**nuget.org**として、**パッケージ ソース**、必要な参照アセンブリに一致する NuGet パッケージ名の検索 (たとえば: Microsoft.VisualStudio.Shell.14.0) にインストールし、プロジェクトです。  NuGet は、初期のアセンブリの依存関係を満たすために複数の参照アセンブリを追加することがあります。  
  
     VS SDK をインストールすることですべての VS SDK の参照アセンブリが一度に追加できる場合は、[メタ パッケージ](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)です。  
  
5.  VS SDK ビルド ツールのバージョンの NuGet 使用に切り替えることもできます。 この NuGet パッケージは[Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools)に追加したら、必要なツールを含めるし、ターゲット VS SDK をインストールせずにコンピューターで、機能拡張プロジェクトをビルドできるようにファイルは、プロジェクト。  
  
> [!NOTE]
>  NuGet の参照アセンブリおよびツールを使用する既存の機能拡張プロジェクトを更新することが必要です。  参照アセンブリ、VS SDK と共にインストールされるツールを使用してビルドを継続できます。