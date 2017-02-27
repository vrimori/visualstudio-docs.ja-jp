---
title: "方法: Visual Studio 2015 への機能拡張プロジェクトの移行 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK をアップグレードします。"
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 方法: Visual Studio 2015 への機能拡張プロジェクトの移行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

拡張機能をアップグレードする方法を次に示します。  
  
> [!IMPORTANT]
>  以前のバージョンの Visual Studio の拡張機能ソリューションのバージョンを管理する場合は、アップグレードする前に、コピーを作成することを確認します。 アップグレードされたバージョンを前の状態に戻すことが困難がある可能性があります。  
  
#### 拡張機能ソリューションをアップグレードするには  
  
1.  アップグレードするには、新しいバージョンでは開く、コピーを使用します。 アップグレードを元に戻すことがないことを伝えられます。  
  
2.  アップグレードの完了後は、devenv.exe の新しいバージョンに、外部プログラムのパスを変更します。 プロジェクト ノードを右クリックし、 **ソリューション エクスプ ローラー**, を選択し、 **プロパティ**します。**デバッグ** \] タブで、検索して、テキスト ボックス **外部プログラムの開始** は次のようになりますが、Visual Studio 2015 パスに devenv.exe のパスを変更するとします。  
  
     **%ProgramFiles%\\Microsoft visual Studio 14.0\\Common7\\IDE\\devenv.exe**  
  
3.  Microsoft.VisualStudio.Shell.14.0.dll への参照を追加します。 \(でプロジェクト ノードを右クリックし、 **ソリューション エクスプ ローラー** にして **追加\/reference**します。 Select、 **拡張** \] タブを確認し、 **Microsoft.VisualStudio.Shell.14.0**.\)  
  
4.  ソリューションをビルドします。 作成済みのファイルにデプロイされます。  
  
     **%LOCALAPPDATA%\\Microsoft\\VisualStudio.14.0Exp\\Extensions\\ \< 作成者名 \> \\ \< プロジェクト名 \> \\ \< プロジェクト \> \\**します。  
  
#### NuGet VS SDK アセンブリを参照する、拡張機能プロジェクトを更新するには  
  
1.  プロジェクトの VS SDK 参照アセンブリを決定します。**ソリューション エクスプ ローラー**, 、プロジェクトの展開 **参照** ノードとプロジェクトの参照の一覧を確認します。  プレフィックスが付いている VS SDK アセンブリを参照 **Microsoft.VisualStudio** 名 \(例: Microsoft.VisualStudio.Shell.14.0\)。  
  
2.  VS SDK 参照アセンブリを選択することで、プロジェクトから削除を右クリックし、 **削除**します。  
  
3.  VS SDK 参照アセンブリの NuGet バージョンを追加します。**ソリューション エクスプ ローラーの参照** ノードが、開いた、 **NuGet パッケージの管理...** ダイアログ。  このダイアログ ボックスについて説明する場合は、「 [NuGet パッケージを使用して管理ダイアログ](http://docs.nuget.org/Consume/Package-Manager-Dialog)します。 VS SDK 参照アセンブリの発行は \[ [nuget.org](http://www.nuget.org) によって [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)します。  
  
4.  使用して **nuget.org** として、 **パッケージ ソース**, 、必要な参照アセンブリに一致する NuGet パッケージの名前を検索 \(例: Microsoft.VisualStudio.Shell.14.0\) し、プロジェクトにインストールします。  NuGet は、初期のアセンブリの依存関係を満たすために複数の参照アセンブリを追加することがあります。  
  
     VS SDK をインストールすることによって、すべての VS SDK 参照アセンブリが一度に追加できる場合は、 [メタ パッケージ](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)します。  
  
5.  VS SDK ビルド ツールの NuGet バージョンを使用してに切り替えることもできます。 この NuGet パッケージは [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) に追加したら、プロジェクトが必要なツールを含めるし、ターゲットのファイルをコンピューターにインストールされている VS SDK を使用しない機能拡張プロジェクトを作成できます。  
  
> [!NOTE]
>  NuGet の参照アセンブリおよびツールを使用する既存の機能拡張プロジェクトを更新することが必要です。  参照アセンブリおよび VS SDK と共にインストールされるツールを使用して、ビルドを続行できます。